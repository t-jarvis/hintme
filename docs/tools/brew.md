---
layout: default
title: Brew
parent: Tools IDE
---

# Brew
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}



---

### Merge --squash
Assume your bug fix branch is called **bugfix** and you want to merge it into **master**.


This will take all the commits from the bugfix branch, squash them into 1 commit, and merge it with your master branch.

```markdown
$ git checkout master
$ git merge --squash bugfix
$ git commit
```