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
xhost +
docker run -it --rm dresantos/gatling recorder
```


Mount configuration and simulation files from host machine and launch recorder in X11

```
docker run -it -e DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix \
-v $HOME/gatling/gatling/conf:/opt/gatling/conf \
-v $HOME/gatling/user-files:/opt/gatling/user-files \
-v $HOME/gatling/results:/opt/gatling/results \
--rm -p 8000:8000 dresantos/gatling recorder
```
