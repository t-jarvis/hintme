---
layout: default
title: Tools IDE
nav_order: 8
permalink: /docs/tools
# has_children: true
---

# Brew
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---
### MacOS

1. Iterm2 [https://iterm2.com/](https://iterm2.com/){:target="_blank"}
2. Oh-my-zh [https://github.com/ohmyzsh/ohmyzsh](https://github.com/ohmyzsh/ohmyzsh){:target="_blank"}
3. zsh-autosuggestions [https://github.com/zsh-users/zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions){:target="_blank"}

4. Autojump [https://github.com/wting/autojump](https://github.com/wting/autojump){:target="_blank"}


A cd command that learns - easily navigate directories from the command line
{: .text-epsilon}

{: .no_toc }
```markdown
$ brew install autojump
```

### Best alias.

```markdown
# show log git pretty.
alias mlog="git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

# Show profile AWS
aws configure list-profiles

# Set default AWS
export AWS_PROFILE=Mypet

# show myIP
alias myip="curl http://ipecho.net/plain; echo"
```

### Brew

```markdown
# Change version
brew unlink php@7.4
brew link php@8.0

brew unlink mysql@5.7
brew link mysql

# Where nginx in macos.
cd /opt/homebrew/opt/nginx
```