---
layout: default
title: Multi account
parent: GIT
---

# Multiple SSH Keys settings for different github account
Below is steps show you how to setup multi account on your laptop.
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}


---

### Create different public key
{: .no_toc  }
create different ssh key according the article [Mac Set-Up Git](http://help.github.com/mac-set-up-git/)

```markdown
 $ ssh-keygen -t rsa -C "your_email@youremail.com"
```

Please refer to [github ssh issues](http://help.github.com/ssh-issues/) for common problems.

for example, 2 keys created at:

	~/.ssh/id_rsa_activehacker
	~/.ssh/id_rsa_jexchan

then, add these two keys as following

	$ ssh-add ~/.ssh/id_rsa_activehacker
	$ ssh-add ~/.ssh/id_rsa_jexchan

you can delete all cached keys before

	$ ssh-add -D

finally, you can check your saved keys

	$ ssh-add -l


### Modify the ssh config
{: .no_toc  }
---------------------------------

	$ cd ~/.ssh/
	$ touch config
	$ subl -a config

Then added

	#activehacker account
	Host github.com-activehacker
		HostName github.com
		User git
		IdentityFile ~/.ssh/id_rsa_activehacker

	#jexchan account
	Host github.com-jexchan
		HostName github.com
		User git
		IdentityFile ~/.ssh/id_rsa_jexchan


### Clone your repo and modify your Git config
{: .no_toc  }
#### Option 1
{: .no_toc  }

clone your repo
	`git clone git@github.com:activehacker/gfs.git gfs_jexchan`

`cd gfs_jexchan` and modify `git config`

	$ git config user.name "jexchan"
	$ git config user.email "jexchan@gmail.com" 
 
	$ git config user.name "activehacker"
	$ git config user.email "jexlab@gmail.com" 

or you can have global git config

	$ git config --global user.name "jexchan"
	$ git config --global user.email "jexchan@gmail.com"


then use normal flow to push your code

	$ git add .
	$ git commit -m "your comments"
	$ git push

#### Option 2
{: .no_toc  }

clone your repo `git clone git@github.com-jexchan:activehacker/gfs.git gfs_jexchan`

`cd gfs_jexchan` and modify `git config`

Author: [jexchan](https://gist.github.com/jexchan/2351996)
{: .fs-3}