# Base Docker Image

* [openjdk:8-jdk](https://registry.hub.docker.com/_/openjdk/)

# Docker Tags

* 2.2.3 (latest)


# Installation

* Install [Docker](https://www.docker.com/)

* Get automated build from public registry:

Latest version:

`docker pull dresantos/gatling:latest`

* [Alternatively] Build an image from Dockerfile: `docker build -t="dresantos/gatling" github.com/asantos82/gatling`

# Usage

Runing the container and entering bash

```
docker run -it --rm dresantos/gatling
```

Runing gatling

```
docker run -it --rm dresantos/gatling gatling
```

Runing recorder

```
docker run -it --rm dresantos/gatling recorder
```


Mount configuration and simulation files from host machine and run gatling in interactive mode

```
docker run -it --rm -v /home/core/gatling/conf:/opt/gatling/conf \
-v /home/core/gatling/user-files:/opt/gatling/user-files \
-v /home/core/gatling/results:/opt/gatling/results \
dresantos/gatling
```
