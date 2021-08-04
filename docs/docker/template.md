---
layout: default
title: Population templates
nav_order: 5
parent: Docker
---

# Population templates
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}



---
## Backend NodeJS

```sh
# Use *-alpine 
# Alpine Linux is much smaller than most distribution base images, 
# and thus leads to much slimmer images in general.
# For detail: https://github.com/nodejs/docker-node#nodealpine
FROM node:12.18-alpine as builder

# Create app directory

ENV HOME=/builder/app
WORKDIR /builder/app
# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
# where available (npm@5+)

# You would install dependencies for packages that require node-gyp support on the alpine variant:
#  https://github.com/nodejs/docker-node/blob/master/docs/BestPractices.md
RUN apk add --no-cache --virtual .gyp python make g++ 

COPY package*.json  yarn.lock  ./

RUN yarn

RUN mkdir -p /prod_dep \
  && cp package.json yarn.lock /prod_dep/ \
  && cd /prod_dep \
  && yarn --prod \
  && cd ${HOME}

COPY . .

RUN yarn run build


#============================== BUILD IMAGE FOR PRODUCTION==========================
FROM node:12.18-alpine as production
ENV HOME=/home/app
WORKDIR /home/app
COPY package*.json ./
COPY yarn.lock .


COPY --from=builder /builder/app/dist/ ./dist/
COPY .env .
COPY ./src ./src
COPY --from=builder /prod_dep/node_modules ./node_modules


CMD [ "yarn", "js-start-server" ]
```

## ReactJs

```bash
FROM node:14.1-alpine AS builder

WORKDIR /opt/web
COPY package.json package-lock.json ./
RUN npm install

ENV PATH="./node_modules/.bin:$PATH"

COPY . ./
RUN npm run build

FROM nginx:1.17-alpine
RUN apk --no-cache add curl
RUN curl -L https://github.com/a8m/envsubst/releases/download/v1.1.0/envsubst-`uname -s`-`uname -m` -o envsubst && \
    chmod +x envsubst && \
    mv envsubst /usr/local/bin
COPY ./nginx.config /etc/nginx/nginx.template
CMD ["/bin/sh", "-c", "envsubst < /etc/nginx/nginx.template > /etc/nginx/conf.d/default.conf && nginx -g 'daemon off;'"]
COPY --from=builder /opt/web/build /usr/share/nginx/html
```