# K3s & CodiMD

## What is the project mainly about
### This project consists of two parts.
- The first part help me get familiar with Dockerfile and how to install K3s. 
- While I deployed the CodiMD servie using K8s in the second part. I used several yaml files to accomplish the task.


## What is the project goal
- Build a Docker image and to run the container based on the image which you build on the K3s.
- Implement the app “CodiMD” with “CodiMD” and “postgresql” image by K8s’ Deployments and Pods.


## Purpose of the project goal
- Make me more familiar with Docker and Pod which I build on the K3s.
- Create K8s services to provide service to users.

*** 
Part1
-----
### What is Docker
- Docker is a tool that allows developers, sys-admins etc. to easily deploy their applications in a sandbox (called containers) to run on the host operating system i.e. Linux.
(in this project os is ubuntu 20.04)
- The key benefit of Docker is that it allows users to package an application with all of its dependencies into a standardized unit for software development. 

### Why Docker
- Docker provides the ability to package and run an application in a loosely isolated environment called a container. The isolation and security allow you to run many containers simultaneously on a given host. 
- Containers are lightweight because they don’t need the extra load of a hypervisor, but run directly within the host machine’s kernel. 

### What is K3s
- K3s is a highly available, certified Kubernetes distribution designed for production workloads in unattended, resource-constrained, remote locations or inside IoT appliances.

### Why K3s
- Because the K8s is too big and too complicated for new hand, so we will install K3s instead.
*** 
Part2
-----
### What is K8s (Kubernetes)
- K8s is a portable, extensible, open-source platform for managing containerized workloads and services, that facilitates both declarative configuration and automation. 
- It has a large, rapidly growing ecosystem. Kubernetes services, support, and tools are widely available.

### Why K8s
- In a production environment, you need to manage the containers that run the applications and ensure that there is no downtime.
- Kubernetes provides you with a framework to run distributed systems resiliently.

---------------------------------------

## Install Docker On Ubuntu

**Install docker**
```sh
sudo apt-get install docker.io
```

**Restart docker**
```sh
sudo systemctl enable docker
sudo systemctl restart docker
```

**Docker user guide**
```sh
sudo docker --help
```
**Ps:**
```sh
 Docker common command: 
 docker run, docker build, docker ps, and docker create
```
---------------------------------------

## Reference
- Docker: https://docs.docker.com/get-docker/
- K3s: https://k3s.io/, &ensp; https://rancher.com/docs/k3s/latest/en/quick-start/
- K8s: https://kubernetes.io/docs/home/


