---
title: Installing Avalon Using Docker
summary: "Instructions for installing an instance of the Avalon Media System on a server using Docker."
sidebar: avalon6_sidebar
permalink: avalon6_installing_avalon_using_docker.html
folder: avalon6
---

## On Linux

1. Install [Docker](https://docs.docker.com/engine/installation/linux/centos/)
2. Install [Docker-Compose](https://docs.docker.com/compose/install/)
3. From inside the `avalon-docker` directory:
    1. `docker-compose pull` to get the prebuilt images from [Dockerhub](https://github.com/avalonmediasystem/avalon-docker/blob/master/dockerhub.com)
    2. `docker-compose up` to stand up the stack

## On Mac

1. Install [Docker Toolbox for OS X](https://www.docker.com/products/docker-toolbox)
2. Run:
    1. `docker-machine stop default`
    2. `docker-machine start default`
    3. `docker-machine env`
    4. `eval $(docker-machine env)`
    5. `docker-machine start default`
    6. `docker-compose up`

The docker container will be accessible via `http://192.168.99.100:8888/`

If anytime OS X says docker is not started, rerun `eval $(docker-machine env)`

## Notes

* `docker-compose logs <service_name>` to see the container(s) logs
* `docker-compose build --no-cache <service_name>` to build the image(s) from scratch
* `docker ps` to see all running containers
* `docker exec -it avalondocker_avalon_1 /bin/bash` to log into Avalon docker container

{% include links.html %}
