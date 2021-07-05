---
layout: default
title: Linux
nav_order: 7
---

# Linux
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

### Transfer files between servers.

 Use it when you want to copy some files between servers.
{: .no_toc }

```markdown
rsync -avzhe ssh  --progress  /localPathServer  username@<IP>:/remotePathServer 
```
