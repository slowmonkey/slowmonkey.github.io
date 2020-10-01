---
layout: post
title: "Learning Docker - Smashtest in docker"
categories: [learning, docker]
tags: [learning, docker]
---

Learning how to create a docker container by creating a smashtest setup in docker.

github: [learning-docker](https://github.com/slowmonkey/learning-docker)

{% include repo_card.html reponame="learning-docker" %}

# Pre-requisites

## Windows
- Windows 10 - 1903+
- Docker Desktop
- Docker installed onto your WSL - Linux
- Docker compose installed onto your WSL - Linux

## Linux
- Docker
- Docker compose

# Introduction

To learn docker I chose to "dockerise" an example smashtest test which would run against a browser(s). For this example the browsers and selenium grids(hub) are additional containers the main container communicates with.

# DockerFile

```
FROM node:13.12.0-slim

WORKDIR /code/

COPY ./code/ .
```

For smashtest all I needed was a nodejs container which would run the smashtest node package.  

The only other required code was to copy the smashtest files into the container.

For other containers that I may create in the future the container may need more setup via `RUN`, `CMD` and many other commands against the image to configure the container.

**NOTE:** That the contents of the DockerFile is what is required for a production deployment. A different docker-compose.yml may be required for production specific configuration.

# docker-compose.yml

```
version: "3.7"
services:

  testserver:
    build: .
    image: smashtest-docker
    volumes:
      - ./code/:/code/

  firefox:
    image: selenium/node-firefox:latest
    volumes:
      - /dev/shm:/dev/shm
    depends_on:
      - hub
    environment:
      HUB_HOST: hub

  chrome:
    image: selenium/node-chrome:latest
    volumes:
      - /dev/shm:/dev/shm
    depends_on:
      - hub
    environment:
      HUB_HOST: hub

  hub:
    image: selenium/hub:latest
    ports:
      - "4444:4444"
```

cite: [Selenium Grid via docker-compose](https://github.com/SeleniumHQ/docker-selenium)

I copied the example docker-compose.yml in the above link for Version 3. Alterations I made were to use a later docker-compose version and to add my testserver service.

For the test server I added the following:
- named the service: `testserver`
- specified the container is build from `.`(the current) directory.
- image name is: `smashtest-docker`
- volume is mapped bi-directionally from the host to the container. This was done for easier development purposes for adding, updating, and deleting any *.smashtest files and smashtest.json configurations.

# How-to Run

1. `docker-compose down` - to ensure nothing is left over.
2. `docker-compose build` - to build the container
3. `docker-compose up -d` - Run's a container with node and smashtest code.
4. `docker-compose run --rm testserver npx smashtest` - Executes the `npx smashtest` command against the docker-compose'd container.

# How-to Clean-up

**NOTE** This will delete all containers and images. If you want a more targetted clean up specify each container and image.

1. `docker-compose down`
2. `docker container prune -f`
3. `docker image prune -f --all`

# Next Steps

- Docker Swarm Deployment