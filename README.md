# Docker Cheat Sheet
This tutorial is meant for those who are interested in learning Docker as a container service. This product is been used extensively in the industry and is really making an impact on the development of various new generation applications. So anyone who is interested in learning basic Docker should can go through it.

This tutorial is compiled taking a reference from [Docker Website](www.docker.com//).

## Table of Contents
* [What is Docker](#what-is-docker)
* [Prerequisites](#Prerequisites)
* [Docker Image](#docker-image)
* [Docker Container](#docker-container)
* [Docker Registry](#docker-registry)
* [Docker Installation](#docker-install)


## What is Docker
Docker is a container management service. The keywords of Docker are develop, ship and run anywhere. The whole idea of Docker is for developers to easily develop applications, ship them into containers which can then be deployed anywhere.

Which means you can dockerize your application and can run on any independent platform, your application is not dependent on any operating system or environment.

## Prerequisites
Readers should be familiar with the basic concepts of Windows should be from IT background In addition, it would help if the readers have some exposure to Linux.

## Docker Image
Docker Images is a template which is use to create Docker Containers, These Docker Images are created using Build command.
Docker let the development community to create and share the software Docker images, You don't need to worry about whether your computer can run the software, Docker images and containers can always run it.\

We will explore more in depth in "Docker Commands Section". 

## Docker Container
Docker Container are the running instance of Docker images and Docker images can run using the Docker run command.

## Docker Registry
Docker Registry is a platform where you can store your Docker Images, This registry could be user's local repository or public(i.e Docker Hub).

Multiple users can share, collaborate and exchange Docker Images by uploading them on docker registry.

A user can pull/push the Docker Images from Docker Registry and deploy on any enviroment.

## Docker Installation
You can install standalone docker on you local machine from [Docker Desktop](https://docs.docker.com/desktop/) for your windows/mac./

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

 
