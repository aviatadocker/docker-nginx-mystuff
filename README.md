# docker-nginx-mystuff
nginx Docker container configured to forward from a VM to mystuff.
Based on dockerfile/nginx https://github.com/dockerfile/nginx


## Nginx Dockerfile


This repository contains **Dockerfile** of [Nginx](http://nginx.org/) for [Docker](https://www.docker.com/)'s [automated build](https://registry.hub.docker.com/u/dockerfile/nginx/) published to the public [Docker Hub Registry](https://registry.hub.docker.com/).


### Base Docker Image

* [dockerfile/ubuntu](http://dockerfile.github.io/#/ubuntu)


### Installation

1. Install [Docker](https://www.docker.com/).

2. Download [automated build](https://registry.hub.docker.com/u/aviata/nginx-mystuff/) from public [Docker Hub Registry](https://registry.hub.docker.com/): `docker pull aviata/nginx-mystuff`

   (alternatively, you can build an image from Dockerfile: `docker build -t="aviata/nginx-mystuff" github.com/aviata/docker-nginx-mystuff`)

### Usage

The "othercontainer" should be listening on port 9000.

    docker run -d -p 80:80 --link othercontainer:mystuff aviata/nginx-mystuff

#### Attach persistent/shared directories

    docker run -d -p 80:80 --link othercontainer:mystuff -v <certs-dir>:/etc/nginx/certs -v <log-dir>:/var/log/nginx -v <html-dir>:/var/www/html aviata/nginx-mystuff

After few seconds, open `http://<host>` to see the welcome page.
