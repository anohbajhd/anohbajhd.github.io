
+++
date = '2025-07-13T12:15:56+05:00'
title = "Modern Infrastructure – Part 1: Docker"
description = "A Deep Dive into Containerization and Development Simplicity 🐳"
tags = ['dockers', 'containers', 'DevOps', 'CI/CD']
+++


> “Build once, run anywhere.”

> That’s not a dream - that’s Docker.


##  What is Docker? 
**Docker** is an open-source platform that allows you to develop, ship, and run applications inside containers. Containers package your app along with its environment, dependencies, and tools - making them portable, lightweight, and consistent across all platforms.

## Why Docker? 
 **Traditional VMs vs Docker**

| Feature               | Traditional VM              | Docker                          |
|-----------------------|-----------------------------|----------------------------------|
| OS Architecture       | Heavy OS per VM             | Shared kernel, lightweight       |
| Boot Time             | Slower boot time            | Fast boot/startup                |
| Resource Usage        | More resources used         | Less CPU/RAM needed              |
| Portability           | Hard to move                | Easy to share or deploy          |

Use Docker when you want to:
- Avoid "It works on my machine"
- Speed up development and CI/CD
- Build microservices
- Scale easily

---

## Docker Architecture
### Core Components:

- `Docker Host:` Docker Host or Docker Engine is the brain of docker. It conatians docker daemon that runs in the background, manages Docker objects (containers, images, networks).

- `Docker Client:` The command-line interface to talk to the daemon.

- `Docker Objects:` It includes:
  - **Images:** Blueprint for containers/app
  - **Containers:** running instances of app
  - **Volumns:** Storing persistent data into host system
  - **Network:**

- `Docker Registries:` Central hubs for sharing /storing images (like Docker Hub, GitHub etc).

![command screenshot](/docker/da.png)

```plaintext
Developer → Docker CLI → Docker Daemon → Container → Application
```

---

## Installing Docker 
### Ubuntu:

```bash
sudo apt update
sudo apt install docker.io
sudo systemctl start docker
sudo systemctl enable docker
```

Check version:
```bash
docker --version
```
Enable running without sudo:

```bash
sudo usermod -aG docker $USER
```
---

### Manjaro KDE:
1. Update your system and install docker:
![command screenshot](/docker/s1.png)

2. Enable docker and check version:
![command screenshot](/docker/s2.png)

---

## Basic Docker Commands
### Working with Images
1. Create a **Dockerfile** (Script to create an image):

![command screenshot](/docker/s18.png)

2. Build an image from dockerfile:
![command screenshot](/docker/s4.png)
![command screenshot](/docker/s5.png)

3. Delete an image:
![command screenshot](/docker/s9.png)

### Working with Containers
1. Run a container from an image:
![command screenshot](/docker/s16.png)
`Note:` You cannot create two containers with same name.

Open browser http://localhost:8080 , you'll see:
![command screenshot](/docker/s6.png)


2. List active containers: 
![command screenshot](/docker/s7.png)

3. List all containers (including stopped ones):
![command screenshot](/docker/sb.png)

4. Stop a running container or remove a container:
![command screenshot](/docker/db.png)


6. Delete all containers at once:
![command screenshot](/docker/s15.png)

---

## Introduction to Docker Compose
### What is Docker Compose?

**Docker Compose** is a tool to define and manage multi-container applications.

Instead of running containers manually one by one, you define them in a docker-compose.yml file and start them all with a single command.

A sample docker compose.yml file:
![command screenshot](/docker/sd.png)

---

## Installation of Docker Compose 
1. Install docker compose:
![command screenshot](/docker/s10.png)
2. Verify if installation is successful:
![command screenshot](/docker/sa.png)

3. Rebuild images and start containers in background:
![command screenshot](/docker/x.png)

4. Lists the containers (services) that are running (or have been created) using your docker-compose.yml file:
```bash
docker compose ps
```
5. Stops all running containers defined in your Compose file, but does not remove them:
```bash
docker compose stop
```
6. Starts containers that were previously stopped using:
```bash
docker compose start
```
7. Stops and removes all the containers, networks, and by default also volumes that were created by:
![command screenshot](/docker/sa.png)

---


## Docker vs Kubernetes 
| Feature     | Docker                   | Kubernetes                          |
|-------------|--------------------------|--------------------------------------|
| **Purpose** | Containerization         | Orchestration                        |
| **Scale**   | Manual                   | Auto-scaling, rolling updates        |
| **Networking** | Simple                | Complex but powerful                 |
| **Use case** | Dev & CI/CD             | Production, large systems            |

---

## Real-World Use Cases 
- `CI/CD Pipelines:` **Jenkins + Docker**

- `Local Dev Environments:` **VSCode devcontainers**

- `Microservices Architecture:` **API Gateway + Services + DB**

- `Edge Computing:` **IoT and Raspberry Pi deployments**

- `App Distribution:` **One image, many platforms**

---

## Conclusion  
Docker is no longer optional - it's essential for modern software development.
Whether you’re building a Node.js app, a Python API, or a full-stack microservice, Docker gives you consistency, speed, and portability.

---

## Bonus: Quick Reference Sheet
```pgsql

sudo systemctl start docker
sudo usermod -aG docker $USER
newgrp docker


docker build -t docker-hello .
docker run -d -p 8080:80 docker-hello

docker ps                     # See running containers
docker ps -a                  # See all containers (even stopped ones)
docker stop hello-container   # Stop a running container 
docker start hello-container  # Start it again
docker rm hello-container     # Remove a container 
docker images                 # List all images 
docker rmi docker-hello       # Remove an image

sudo pacman -S docker-compose

v2 → docker compose up -d
v1 → docker-compose up -d


docker compose ps         # Show running services
Open browser http://localhost:8080
docker compose stop       # Stop all services
docker compose start      # Start them again
docker compose down       # Stop & remove everything



```
