# Docker: cheatsheet tadında
## ⚠ Template, work in progress
## Why did the Docker appear?

Let's assume that we need to run two applications in isolation from each other.

#### Bare-metal

```server = linux + libraries + app #1```

```server = linux + libraries + app #2```

#### Virtualization
  
```server = hypervisor + [ linux + libraries + app #1 ] + [ linux + libraries + app #2 ]```

#### Container (thanks to namespaces and control groups)
  
```server = linux + [ libraries + app #1 ] + [ libraries + app #2 ]```
  
*The containers looks good but they are very difficult to manage.*

#### Docker
  
```server = linux + docker + [ libraries + app #1 ] + [ libraries + app #2 ]```

*The docker layer makes things easier*

## Docker Engine
```Docker Engine``` = ```Docker CLI``` + ```Docker REST API``` + ```Docker Daemon```

## Image and Container
**Image:** Application template

**Container:** Running application instance from the image

```Application Image``` -> ```Running Application Container #1```, ```Running Application Container #2```, ```...```

## Docker CLI

### Try the Docker and get help
```bash
# list all available commands
docker --help

# check the docker version
docker version

# try the docker and run a hello-world
docker container run hello-world
```
### List images and containers
```bash
# list installed images
docker image ls

# list running containers
docker container ls

# list all containers including stopped ones
docker container ls -a
```
### Start a container from an image
```bash
docker container run $LOCATION/$IMAGE

# give a name to the container
docker container run --name $NAME $LOCATION/$IMAGE

# start without connecting to the shell
docker container run -d $LOCATION/$IMAGE
```
### Start an existing container
```bash
docker container start $ID

# and attach it to the shell
docker container start $ID -a
```
### Stop a container
```bash
docker container stop $ID
```
### Remove a container
```bash
# if the container is not running
docker container rm $ID

# force a container to stop and delete it
docker container rm -f $ID
```
### Remove an image
```bash
docker image rm $ID
```
### Connect to a container and manage it
```bash
# connect to it via shell
docker container exec -it $CONTAINER sh

# or
docker container exec -it $CONTAINER bash

# or
docker container exec -it $CONTAINER powershell

# disconnect from the container's shell
exit
```