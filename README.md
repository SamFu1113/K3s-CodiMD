# K3s & CodiMD

## What is the project mainly about?
### This project consists of two parts.
- The first part help me get familiar with Dockerfile and how to install K3s. 
- While I deployed the CodiMD servie using K8s in the second part. I used several yaml files to accomplish the task.


## What is the project goal?
- Build a Docker image and run the container based on the image which I build on the K3s.
- Implement the app “CodiMD” with “CodiMD” and “postgresql” image by K8s’ Deployments and Pods.


## Purpose of the project goal.
- Make me more familiar with Docker and Pod which I build on the K3s.
- Create K8s services to provide service to users.

*** 
Part1
-----
### What is Docker?
- Docker provides the ability to package and run an application in a loosely isolated environment called a **container**.
- The isolation and security allow me to run many containers simultaneously on a given host.
- Containers are lightweight because they don’t need the extra load of a hypervisor, but run directly within the host machine’s kernel.
- This means I can run more containers on a given hardware combination than if I am using virtual machines. 
- I can even run Docker containers within host machines that are actually virtual machines!  
#
- Docker is a tool that allows developers, sys-admins etc. to easily deploy their applications in a sandbox (called containers) to run on the host operating system i.e. Linux.
(in this project os is ubuntu 20.04)
- The key benefit of Docker is that it allows users to package an application with all of its dependencies into a standardized unit for software development. 

![image info](photos/docker_illustration.PNG)

**Additional information**
- Docker provides tooling and a platform to manage the lifecycle of my containers:
	- Develop my application and its supporting components using containers.
	- The container becomes the unit for distributing and testing my application.
	- When I’am ready, deploy my application into my production environment, as a container or an orchestrated service.
### Why choose Docker?
- Docker provides the ability to package and run an application in a loosely isolated environment called a container. The isolation and security allow me to run many containers simultaneously on a given host. 
- Containers are lightweight because they don’t need the extra load of a hypervisor, but run directly within the host machine’s kernel. 

--------
### What is K3s?
- K3s is a highly available, certified Kubernetes distribution designed for production workloads in unattended, resource-constrained, remote locations or inside IoT appliances.

### Why choose K3s?
- Because the K8s is too big and too complicated for new hand, so we will install K3s instead.
*** 
Part2
-----
### What is Kubernetes(K8s)?
- K8s is a portable, extensible, open-source platform for managing containerized workloads and services, that facilitates both declarative configuration and automation. 
- It has a large, rapidly growing ecosystem. Kubernetes services, support, and tools are widely available.

### Why choose K8s?
- In a production environment, I need to manage the containers that run the applications and ensure that there is no downtime.
- Kubernetes provides me with a framework to run distributed systems resiliently.

### What is CodiMD?
- CodiMD is the free software version of [HackMD](https://hackmd.io/), developed and opened source by the HackMD team with reduced features (without book mode), I can use CodiMD for the community and own all my data.
- (See the [origin of the name CodiMD](https://github.com/hackmdio/codimd/issues/720).)

### Why choose CodiMD?
- CodiMD is perfect for open communities, while HackMD emphasizes on permission and access controls for commercial use cases.
- HackMD team is committed to keep CodiMD open source. All contributions are welcome!
---------------------------------------

## Install Docker on Ubuntu 20.04


**Install Docker**
```sh
sudo apt-get install docker.io
```

**Restart Docker**
```sh
sudo systemctl enable docker
```
```sh
sudo systemctl restart docker
```

**Docker user guide**
```sh
sudo docker --help
```
**Ps:**
**Docker common command:**</br>
```sh
docker run
```
```sh
docker build
```
```sh
docker ps
```
```sh
docker create
```

---------------------------------------

## Install K3s on Ubuntu 20.04

**Install K3s**
```sh
curl -sfL https://get.k3s.io | INSTALL_K3S_EXEC="--docker --write-kubeconfig-mode 644 " sh -
```

**Check whether K3s is running without error**
```sh
kubectl get all -A
```

## K8s introduction

**Pod**</br>
&nbsp;&nbsp;&nbsp;&nbsp;Pods are the smallest deployable units of computing that I can create and manage in Kubernetes. A Pod is a group of one or more containers, with shared storage/network resources, and a specification for how to run the containers.

**Deployments**</br>
&nbsp;&nbsp;&nbsp;&nbsp;A Deployment provides declarative updates for Pods ReplicaSets. I describe a desired state in a Deployment, and the Deployment Controller changes the actual state to the desired state at a controlled rate. I can define Deployments to create new ReplicaSets, or to remove existing Deployments and adopt all their resources with new Deployments.
	
**Services**</br>
&nbsp;&nbsp;&nbsp;&nbsp;An abstract way to expose an application running on a set of Pods as a network service. With Kubernetes I don’t need to modify my application to use an unfamiliar service discovery mechanism. Kubernetes gives Pods their own IP addresses and a single DNS name for a set of Pods, and can load-balance across them.


## Project implementation

### Part I
> &nbsp;&nbsp;&nbsp;&nbsp;To make me familiar with Docker and Pod, this homework topic is to build a Docker image and to run the container based on the image which I build on the K3s.

**Goal**: Build a gcc Docker image that print “hello, this is lab 04.” and running on the K3s.

|  Steps  |  Description   |
|  ----  | ----  |
| **Step 1**  | Create a C language file that print "hello, this is lab 04." |
| **Step 2**  | Write a Dockerfile based on "gcc:10.2" image. |
| **Step 3**  | Build a Docker image whose name is "gcc:lab04". |
| **Step 4**  | Write a Pod yaml file that is running "gcc:lab04" image. |









### Part II
> &nbsp;&nbsp;&nbsp;&nbsp;Implement the app “CodiMD” with “CodiMD” and “postgresql” image by K8s’ Deployments and Pods, while create K8s’ Services to provide service to users.<br/>

Hints: [CodiMD github](https://github.com/hackmdio/codimd), [CodiMD Documentation](https://hackmd.io/c/codimd-documentation/%2Fs%2Fcodimd-documentation)

**For example, using docker-compose to setup CodiMD**
- Below is the **Dockerfile** example 
	- Dockerfile
<!---
(I didn't actually use it, just for demonstration.)
--->
	
```sh
version: "3"
services:
  database:
    image: postgres:11.6-alpine  
    environment:
      - POSTGRES_USER=codimd
      - POSTGRES_PASSWORD=change_password
      - POSTGRES_DB=codimd
    volumes:
      - "database-data:/var/lib/postgresql/data"
    restart: always
  codimd:
    image: nabo.codimd.dev/hackmdio/hackmd:2.2.0  
    environment:
      - CMD_DB_URL=postgres://codimd:change_password@database/codimd
      - CMD_USECDN=false
    depends_on:
      - database
    ports:
      - "3000:3000"
    volumes:
      - upload-data:/home/hackmd/app/public/uploads
    restart: always
volumes:
  database-data: {}
  upload-data: {}
```
- According to the docker-compose file, I finished the work to create CodiMD service.

- The following images are the hints for the implementation.
	- **deployment.yaml**:  
		![image info](photos/deployment.PNG)
	- **deployment_db.yaml**:  
		![image info](photos/deployment_db.PNG)
	- **service.yaml**:  
		![image info](photos/service.PNG)
	- **service_db.yaml**:  
		![image info](photos/service_db.PNG)
		
- According to the hints about yamls, I finished the work to deploy CodiMD service.
---------------------------------------


## References
- Docker: https://docs.docker.com/get-docker/
- K3s: https://k3s.io/, https://rancher.com/docs/k3s/latest/en/quick-start/
- K8s: https://kubernetes.io/docs/home/
- CodiMD: [CodiMD github](https://github.com/hackmdio/codimd), [CodiMD Documentation](https://hackmd.io/c/codimd-documentation/%2Fs%2Fcodimd-documentation) 


