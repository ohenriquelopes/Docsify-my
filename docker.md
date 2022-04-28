# Docker

## Basic commands

```
Used to pull images from the docker repository (hub.docker.com)
- docker pull <image name>

Used to create a container from an image
- docker run -it -d <image name>

Used to list the running containers
- docker ps

Used to show all the running and exited containers
- docker ps -a

Used to show only containers ids
- docker ps -q

Used to access the running container
- docker exec -it <container id> bash

Used to stop a running container
- docker stop <container id>

Used to stop container immediately
- docker stop -t 0

Used to delete all containers
- docker container prune

Used to kill container, stop immediately
- docker kill <container kill>

Used to create a new image of an edited container on the local system
- docker commit <container id> <username/imagename>

Used to login in docker hub
- docker login

Used to push an image in to the docker hub repository
- docker push <username/image name>

Used to list all the locally sotred docker images
- docker images

Used to remove all images
- docker rmi -f $(docker images -aq) 

Used to delete a stopped container
- docker rm <container id>

Used to delete an image from local storage
- docker rmi <image-id>

Used to build an image from a specified docker file
- docker build <path to docker file>


```

## Docker logs
```
docker logs $ID

docker logs $ID 2>&1 | less

docker logs -f $ID # Follow log output
```

## Docker file
```
Define a image
- FROM nginx:latest

Instruction will execute any commands in a new layer on top of the current image 
and commit the results
- RUN apt-get update && apt-get install -y vim
- RUN ["sh", "-c", "echo $HOME"]
- RUN <command>
- RUN ["executable", "param1", "param2"]

The main purpose of a CMD is to provide defaults for an executing container
- CMD ["executable", "param1", "Param2"]
- CMD ["param1", "param2"]
- CMD command param1 param2 (shell form)

This instruction informs Docker that the container listens on the specified network 
ports at runtime
- EXPOSE <port> [<port>/<protocol>...]
- EXPOSE 80/tcp
- docker run -p 80:80/tcp -p 80:80/udp ..

This instruction copies new files or directories from and adds them to the 
filesystem of the container at the path
- COPY [--chown=<user:<group>] <src> ... <dest>
- COPY [--chown=<user:<group>] ["<src>", ... "<dest>"]
- COPY test.txt relativeDir/
- COPY test.txt /absolutDir/

You can use the exec form of to set fairly stable default commands and arguments 
and then use either form of to set additional defaults that are more likely to be changed.
- ENTRYPOINT ["top", "-b"]

This instruction creates a mount point with the specified name and marks it as 
holding exeternally mounted volumes from native host or other containers.
- VOLUME ["/data"]

This instruction sets the user name(or UID) and optionally the user group(or GID) 
to use when running the image and for any, and instructions that follow it in the 
(user, run, cmd, entrypoint)
- USER <user>[:<group>]
- USER <UID>[:<GID>]

This instruction sets the working directory for any and instruction that 
follow it in the . if the doesn't exist, it will be created even if it's not used in any 
subsequent instruction
(workdir, run, cmd, entrypoin, copy, add)
- WORKDIR /path/to/workdir


```
