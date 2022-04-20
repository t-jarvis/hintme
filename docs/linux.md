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

SSH tunnel
{: .no_toc }

```markdown
ssh -N -L IPlocal:3306:IPRemote:3306 userName@IPRemote
```

List port

```markdown
lsof -i tcp:3000
```

