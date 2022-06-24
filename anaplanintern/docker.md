---
description: Tool for running app in isolated environment
---

# Docker

## Container

Abstraction at the app layer that packages **code** and **dependencies** together. Multiple containers can run on **SAME** machine, each as an **ISOLATED** process

* A running instance of an Image

## Virtual Machines

Abstraction of physical hardware-->turn one server into many. Full copy of OS, app, and libraries; Takes up huge space and slow to boot

## Docker Image

* Template for creating an environment
* Snapshot
* Has everything need to run app (OS, Software, App code)

## General Process

1. Pull official Images from Docker Hub: `docker pull nginx` and check all Images`: docker images`
2. Run a container in Image: `docker run -d -p 8080:80 nginx:latest;` "latest" is the TAG and needed
3. Check all containers running: `docker container ls`
4. Remove container: `docker rm [ID/NAME]` / `docker rm $(docker ps -aq)` / `docker rm -f $(docker ps -aq)`

## Exposing Port

* The container is running with a port of 80
* Host issue request of localhost:8080 mapped to PORT 80 in container --> run -p 8080:80 when running the container
* Open up browser and go to localhost:8080 to get the container's application's page
* Multiple hosts to one port: `-p 8080:80 -p 3000:80`

## Naming Container

* `docker run --name website -d -p 3000:80 -p 8080:80 nginx:latest` Specify the name, easier to identify and stop

## Volumes

Allow sharing of data, files, and folders

* Hosts and container form Volumes
* Create file locally: website/index.html (website is a folder)
* `docker run --name website -v $(pwd):/usr/share/nginx/html:ro -d -p 8080:80 nginx:latest.` In this way, we serve the container with our local file (ro Read Only flag can be removed in order to write into container)
* `docker exec -it website bash`. In this way, we will be inside the container. Go to usr/share/nginx/html to make changes, and these changes will be on local machine as well

## Share Volumes Between Containers

* `docker run --name website-copy --volumes-from website -d -p 8081:80 nginx:latest.` In this way, we use the data from website container to serve the website-copy container.&#x20;

## DockerFile

Create our own images

{% embed url="https://docs.docker.com/engine/reference/builder/" %}

* Create a file called "Dockerfile" in the root directory of project

```docker
FROM nginx:latest
ADD . /usr/share/nginx/html
```

* `docker build --tag website:latest .` (. stands for current directory, this is where to look for a Dockerfile)
* Can use node.js and express framework to make a simple backend server

```docker
FROM node:latest
WORKDIR /app
ADD . .
RUN npm install
CMD node index.js
```

* Go into your local node.js app folder: `docker build --tag user-api:latest .`
* `docker run --name user-api -d -p 3000:3000 user-api:latest` This runs the container

### .dockerignore

```docker
node_modules
Dockerfile
.git
folder/**
```

## Layer and Cache

Use cache to boost performance: A source file change shouldn't trigger all things to rebuild

```docker
FROM node:latest
WORKDIR /app
ADD package*.json ./ 
RUN npm install
ADD . .
CMD node index.js
```

In this way, adding package.json & package-lock.json into the container is using cache since these two files are not changing.
