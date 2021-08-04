---
layout: default
title: Nginx
nav_order: 4
has_children: true
---

# Nginx
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}


---
## Check status of nginx

```bash
nginx -t
```
## Start or Stop Nginx

Using for Ubuntu.

```bash
# Stop nginx
$ /etc/init.d/nginx stop

# Start nginx
$ /etc/init.d/nginx start
```

Case Nginx installed by brew.

Please refer to [Homebrew page](https://brew.sh/){:target="_blank"} for Brew.
{: .fs-3 }

```bash
# Stop nginx
$ brew services stop nginx

# Start nginx
$ /etc/init.d/nginx start
```