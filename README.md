# Docker Cheat Sheet
This tutorial is meant for those who are interested in learning Docker as a container service. This product is been used extensively in the industry and is really making an impact on the development of various new generation applications. So anyone who is interested in learning basic Docker should can go through it.

This tutorial is compiled taking a reference from [Docker Website](https://www.docker.com//).

## Table of Contents
* [What is Docker](#what-is-docker)
* [Prerequisites](#Prerequisites)
* [Docker Image](#docker-image)
* [Docker Container](#docker-container)
* [Docker Registry](#docker-registry)
* [Docker Installation](#docker-install)
* [Dockerfile](#docker-file)
* [Docker Commands](#docker-commands)


## What is Docker
Docker is a container management service. The keywords of Docker are develop, ship and run anywhere. The whole idea of Docker is for developers to easily develop applications, ship them into containers which can then be deployed anywhere.

Which means you can dockerize your application and can run on any independent platform, your application is not dependent on any operating system or environment.

## Prerequisites
Readers should be familiar with the basic concepts of Windows should be from IT background In addition, it would help if the readers have some exposure to Linux.

## Docker Image
Docker Images is a template which is use to create Docker Containers, These Docker Images are created using Build command.
Docker let the development community to create and share the software Docker images, You don't need to worry about whether your computer can run the software, Docker images and containers can always run it.

We will explore more in depth in "Docker Commands Section". 

## Docker Container
Docker Container are the running instance of Docker images and Docker images can run using the Docker run command.

## Docker Registry
Docker Registry is a platform where you can store your Docker Images, This registry could be user's local repository or public(i.e Docker Hub).

Multiple users can share, collaborate and exchange Docker Images by uploading them on docker registry.

A user can pull/push the Docker Images from Docker Registry and deploy on any enviroment.

## Docker Installation
You can install standalone docker on you local machine from [Docker Desktop](https://docs.docker.com/desktop/) for your windows/mac.

Then you can start Docker Tool Box, command propmt will open to check docker is running run below command.
```
docker --version
```
Or if you are using AWS Linux EC2 instance you can simply execute below command to install Docker.
```
sudo amazon-linux-extras install docker
```
To enable and start Docker service on startup in AWS Linux EC2 instance use below command.
```
sudo systemctl enable docker
```
To add your user to docker group use below command:
```
sudo usermod-a -G docker <user>
```
## Dockerfile
Docker gives us facility to pull the images directly from Docker Hub but if you want to create custom Image you can do by writing your own Dockerfile. A Docker File is a simple text file with instructions on how to build your images.

Sample Dockerfile below:
```
#This is a sample Dockerfile 
FROM ubuntu
MAINTAINER ishaansolanki6@gmail.com 

RUN apt-get update 
RUN apt-get install –y nginx 
CMD [“echo”,”Image created”] 
```

### Instructions
* [FROM](https://docs.docker.com/engine/reference/builder/#from) Sets the Base Image for subsequent instructions.
* [MAINTAINER (deprecated - use LABEL instead)](https://docs.docker.com/engine/reference/builder/#maintainer-deprecated) Set the Author field of the generated images.
* [RUN](https://docs.docker.com/engine/reference/builder/#run) execute any commands in a new layer on top of the current image and commit the results.
* [CMD](https://docs.docker.com/engine/reference/builder/#cmd) provide defaults for an executing container.
* [EXPOSE](https://docs.docker.com/engine/reference/builder/#expose) informs Docker that the container listens on the specified network ports at runtime.  NOTE: does not actually make ports accessible.
* [ENV](https://docs.docker.com/engine/reference/builder/#env) sets environment variable.
* [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#entrypoint) configures a container that will run as an executable.
* [WORKDIR](https://docs.docker.com/engine/reference/builder/#workdir) sets the working directory.
* [LABEL](https://docs.docker.com/config/labels-custom-metadata/) apply key/value metadata to your images, containers, or daemons.

## Docker Commands
- Command to create an image via Dockerfile:
```
$ docker build -t nginx .
```
(-t) represents the tag </br>
(.) repesents the current directory for Dockerfile

- Command to list the Images 
```
$ docker images
```
```
REPOSITORY                TAG                 IMAGE ID            CREATED             SIZE
ubuntu                    latest              77af4d6b9913        19 hours ago        1.089 GB
nginx                     latest              b6fa739cedf5        19 hours ago        1.089 GB
```

For every image Hash sha256 of the source code is stored which will be unique number called as IMAGE ID

- Commant to list images by Name
```
$ docker images java

REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
java                8                   308e519aac60        6 days ago          824.5 MB
java                7                   493d82594c15        3 months ago        656.3 MB
java                latest              2711b1d6f3aa        5 months ago        603.9 MB
```

- Commant to list images by Tag 
```
$ docker images java:8

REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
java                8                   308e519aac60        6 days ago          824.5 MB
```
