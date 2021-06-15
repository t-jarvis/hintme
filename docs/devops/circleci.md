---
layout: default
title: CircleCI
parent: CI/CD
nav_order: 1
grand_parent: Devops

---

# CircleCI
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}
----
### About
[About CircleCI](https://circleci.com/docs/2.0/about-circleci/?section=getting-started) 
{: .fs-2}

Hmm. Please help me contribute this part.
{: .fs-6}


```yml
version: 2.1

# Define the jobs we want to run for this project
jobs:
  build:
    docker:
      - image: circleci/<language>:<version TAG>
        auth:
          username: mydockerhub-user
          password: $DOCKERHUB_PASSWORD  # context / project UI env-var reference
    steps:
      - checkout
      - run: echo "this is the build job"
  test:
    docker:
      - image: circleci/<language>:<version TAG>
        auth:
          username: mydockerhub-user
          password: $DOCKERHUB_PASSWORD  # context / project UI env-var reference
    steps:
      - checkout
      - run: echo "this is the test job"

# Orchestrate our job run sequence
workflows:
  build_and_test:
    jobs:
      - build
      - test:
          requires:
            - build
```