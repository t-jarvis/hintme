---
layout: default
title: Docker
parent: Devops
has_children: true
nav_order: 2
---

# Docker
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}



---
## Cheatsheet

### Docker start
Start/stop a container.
{: .no_toc }

```markdown
docker start [options] CONTAINER
  -a, --attach        # attach stdout/err
  -i, --interactive   # attach stdin

docker stop [options] CONTAINER

## E.g
```

---
### Docker build
Create an image from a Dockerfile.
{: .no_toc }

```markdown
docker build [options] .
  -t "app/container_name"    # name
  --build-arg APP_HOME=$APP_HOME    # Set build-time variables

## E.g
```
---

### Docker create

Code can be rendered inline by wrapping it in single back ticks.

Lorem ipsum dolor sit amet, `<inline code snippet>` adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.

{: .no_toc }

```markdown
docker create [options] IMAGE
  -a, --attach               # attach stdout/err
  -i, --interactive          # attach stdin (interactive)
  -t, --tty                  # pseudo-tty
      --name NAME            # name your image
  -p, --publish 5000:5000    # port map (host:container)
      --expose 5432          # expose a port to linked containers
  -P, --publish-all          # publish all ports
      --link container:alias # linking
  -v, --volume `pwd`:/app    # mount (absolute paths needed)
  -e, --env NAME=hello       # env vars

## E.g
$ docker create --name app_redis_1 \
  --expose 6379 \
  redis:3.0.2
```

---

### Docker exec

Code can be rendered inline by wrapping it in single back ticks.

<div class="code-example" markdown="1">
Lorem ipsum dolor sit amet, `<inline code snippet>` adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.

## Heading with `<inline code snippet>` in it.
{: .no_toc }
</div>
```markdown
docker exec [options] CONTAINER COMMAND
  -d, --detach        # run in background
  -i, --interactive   # stdin
  -t, --tty           # interactive

## E.g
$ docker exec app_web_1 tail logs/development.log
$ docker exec -t -i app_web_1 rails c
```
