---
layout: default
title: GIT
has_children: true
nav_order: 6
---

# GIT
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}



---


### Getting from remote

```markdown
git fetch origin
git checkout --track origin/$branchname
```

### Undo commits to a specific commit

```markdown
git reset --hard $commit_id

# Now push safely to your branch
git push --force-with-lease

# Or push brutally to your branch
git push --force
```
