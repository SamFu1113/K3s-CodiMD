# K3s & CodiMD

## What is K3s
- K3s is a highly available, certified Kubernetes distribution designed for production workloads in unattended, resource-constrained, remote locations or inside IoT appliances.

## What is the goal

- Build a Docker image and to run the container based on the image which you build on the K3s.
- Implement the app “CodiMD” with “CodiMD” and “postgresql” image by K8s’ Deployments and Pods.

## Purpose of the goal

- Make students be familiar with Docker and Pod which you build on the K3s.
- Create K8s’ Services to provide service to users.

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
 Docker common command: docker run, docker build, docker ps, docker create
```

**Reference**
- https://k3s.io/


