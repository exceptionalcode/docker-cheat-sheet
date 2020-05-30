# Docker Cheat Sheet
This tutorial is meant for those who are interested in learning Docker as a container service. This product is been used extensively in the industry and is really making an impact on the development of various new generation applications. So anyone who is interested in learning basic Docker should can go through it.

This tutorial is compiled taking a reference from [Docker Website](https://www.docker.com//).

## Table of Contents
* [What is Docker](#what-is-docker)
* [Prerequisites](#Prerequisites)
* [Docker Installation](#docker-install)
* [Dockerfile](#docker-file)
* [Docker Image](#docker-image)
* [Docker Container](#docker-container)
* [Docker Volume](#docker-volume)
* [Docker Registry](#docker-registry)


## What is Docker
Docker is a container management service. The keywords of Docker are develop, ship and run anywhere. The whole idea of Docker is for developers to easily develop applications, ship them into containers which can then be deployed anywhere.

Which means you can dockerize your application and can run on any independent platform, your application is not dependent on any operating system or environment.


## Prerequisites
Readers should be familiar with the basic concepts of Windows should be from IT background In addition, it would help if the readers have some exposure to Linux.


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

### Create an image via Dockerfile:
```
$ docker build -t nginx .
```
(-t) represents the tag </br>
(.) repesents the current directory for Dockerfile

If the Dockerfile is in different directory
```
$ docker build -t nginx <dir path>/
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


## Docker Image
Docker Images is a template which is use to create Docker Containers, These Docker Images are created using Build command.
Docker let the development community to create and share the software Docker images, You don't need to worry about whether your computer can run the software, Docker images and containers can always run it.


### List Images 
```
$ docker images
```
```
REPOSITORY                TAG                 IMAGE ID            CREATED             SIZE
ubuntu                    latest              77af4d6b9913        19 hours ago        1.089 GB
nginx                     latest              b6fa739cedf5        19 hours ago        1.089 GB
```

> For every image Hash sha256 of the source code is stored which will be unique number called as IMAGE ID

### List Images by Name
```
$ docker images java

REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
java                8                   308e519aac60        6 days ago          824.5 MB
java                7                   493d82594c15        3 months ago        656.3 MB
java                latest              2711b1d6f3aa        5 months ago        603.9 MB
```

### List Images by Tag 
```
$ docker images java:8

REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
java                8                   308e519aac60        6 days ago          824.5 MB
```

### Pull Image from default Registry(Docker Hub)
```
$ docker pull ubuntu
```
> It will pull the ubuntu latest image from Docker Hub

### Pull specific version of Image from Docker Hub
```
$ docker pull ubuntu:18.04
```

### Delete Image by ImageId
```
$ docker rmi <ImageId>
```

### Delete Image by Tag
```
$ docker rmi <Repository>:<Tag>
```
> If you do not give any tag it is going to delete the latest tag

### Delete Image if its container is running
```
$ docker rmi --force <ImageId>
```
If you want to delete image while its container is running

## Docker Container
Docker Container are the running instance of Docker images and Docker images can run using the Docker run command.

### Run Image and to create Container by an Image 
```
$ docker run -p 8080:8080 <image tag>
```
> (-p) represents the port mapping inside the container to expose outside the container 

### Run Image and to create Container by an Image in the Background
```
$ docker run -d -p 8080:8080 <Image Tag>
```

### Run Container and Exited when it is removed or Container in stopped
```
$ docker run --rm -d -p 8080:8080 <Image Tag>
```

### Run Container by giving its Name
```
$ docker run --name nametesing -d -p 8080:8080 <Image Tag>
```

### List all the running Containers on the machine
```
$ docker ps
```

### List all the Containers available on the machine
```
$ docker ps -a
```
> -a represents for all


### Containers Info
On Linux you can move into the the docker container folder where you can find Docker Containers details.
Path for Docker Container folder:
```
$ sudo ls -l /var/lib/docker/containers
```

### Detailed Info for a running Container
```
$ docker inspect <containerId>
```
> This will give you a json output and detailed information about the running container


### Process running inside Container
```
$ docker top <containerId> 
```
> This will show all process running inside container and its process id


### Realtime stats of Container
```
$ docker stats 
```
> This will show Conatiner's memory, cpu, limit usage on realtime


### Container Logs
```
$ docker logs -f <containerId>
```
> -f represents the running follow logs at runtime


### Container Delete/Remove
```
$ docker rm <containerId>
```
> It will also delete the container folder on the above location.


### Stop Container by Container Id
```
$ docker stop <containerId>
```

### Stop Container by Container Name
```
$ docker stop <containerName>
```


## Docker Volume
In Docker, you have a separate volume that can shared across containers. These are known as data volumes.</br>

Some of the features of data volume are: </br>

- They are initialized when the container is created.
- They can be shared and also reused amongst many containers.
- Any changes to the volume itself can be made directly.
- They exist even after the container is deleted.

### Create Volume
```
$ docker volume create jenkins
```
> Here we created volume called jenkins


### List Volume
```
$ docker volume ls
```

### Path for Local Volume available(Linux):
```
$ sudo ls /var/lib/docker/volumes
```
> On this given path you can find local directory created for you container data volume


### Mount the volume while creating a container 
```
docker run -v jenkins:/var/jenkins_home -p 80:8080 jenkins
```
> This is an example of data mounting for jenkins 


## Docker Registry
Docker Registry is a platform where you can store your Docker Images, This registry could be user's local repository or public(i.e Docker Hub).

Multiple users can share, collaborate and exchange Docker Images by uploading them on docker registry.

A user can pull/push the Docker Images from Docker Registry and deploy on any enviroment.
