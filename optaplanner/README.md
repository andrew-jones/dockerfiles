# OptaPlanner

Sharing X Session with docker container to run OptaPlanner.

Tested on Ubuntu 14.04 Desktop

## Build

`docker build -t=optaplanner .`

## Run

### From build image

`docker run -it --rm -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix optaplanner`

### From Docker Hub

`docker run -it --rm -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix andrew-jones/optaplanner`
