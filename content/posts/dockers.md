
+++
date = '2025-07-13T12:15:56+05:00'
title = "Modern Infrastructure – Part 1: Docker"
description = "A Deep Dive into Containerization and Development Simplicity 🐳"
tags = ['dockers', 'containers', 'DevOps', 'CI/CD']
+++


> “Build once, run anywhere.”

> That’s not a dream — that’s Docker.


##  What is Docker? 
Docker is an open-source platform that allows you to develop, ship, and run applications inside containers. Containers package your app along with its environment, dependencies, and tools — making them portable, lightweight, and consistent across all platforms.

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

## Docker Architecture
### Core Components:

- **Docker Daemon:** Runs in the background, manages Docker objects (containers, images, networks).

- **Docker CLI:** The command-line interface to talk to the daemon.

- **Docker Images:** Read-only templates to create containers.

- **Docker Containers:** Running instances of images.

- **Docker Registries:** Central hubs for sharing images (like Docker Hub).

```plaintext
Developer → Docker CLI → Docker Daemon → Container → Application
```
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
## Docker Terminology 
- **Image:** App blueprint

- **Container:** Running image

- **Dockerfile:** Script to create an image

- **Volume:** Persistent storage

- **Port Mapping:** Linking container port to host port

- **Tag:** Version label (myapp:1.0)

- **Registry:** Image storage (Docker Hub, GitHub Packages, etc.)

## Basic Docker Commands 
```bash
# Run a container
docker run -it ubuntu

# List containers
docker ps -a

# Build from Dockerfile
docker build -t myapp .

# Stop a container
docker stop <container_id>

# Remove container/image
docker rm <id> | docker rmi <id>
```

## Dockerfile: Blueprint of Your App 
```Dockerfile
# Sample Node.js app
FROM node:20
WORKDIR /app
COPY . .
RUN npm install
EXPOSE 3000
CMD ["node", "index.js"]
```

Build & Run:

```bash
docker build -t my-node-app .
docker run -p 3000:3000 my-node-app
```

## Docker Compose 
Use Compose to run multi-container apps (e.g. app + database).

docker-compose.yml:

```yaml
version: '3'
services:
  app:
    build: .
    ports:
      - "3000:3000"
  db:
    image: mongo
    ports:
      - "27017:27017"
```

```bash
docker-compose up
```

## Volumes and Bind Mounts <a name="volumes"></a>
- **Volume:** Docker-managed storage (docker volume create)
- **Bind Mount:** Link local path to container

```bash
docker run -v myvolume:/data app
docker run -v $(pwd):/app app
```
## Docker Hub and Registries 
**Docker Hub:** Official public registry

GitHub Container Registry (GHCR) and Harbor are alternatives

```bash
# Push image
docker tag myapp username/myapp
docker push username/myapp
```

## Docker vs Kubernetes 
| Feature     | Docker                   | Kubernetes                          |
|-------------|--------------------------|--------------------------------------|
| **Purpose** | Containerization         | Orchestration                        |
| **Scale**   | Manual                   | Auto-scaling, rolling updates        |
| **Networking** | Simple                | Complex but powerful                 |
| **Use case** | Dev & CI/CD             | Production, large systems            |


## Real-World Use Cases 
- `CI/CD Pipelines:` **Jenkins + Docker**

- `Local Dev Environments:` **VSCode devcontainers**

- `Microservices Architecture:` **API Gateway + Services + DB**

- `Edge Computing:` **IoT and Raspberry Pi deployments**

- `App Distribution:` **One image, many platforms**

## Conclusion  
Docker is no longer optional — it's essential for modern software development.
Whether you’re building a Node.js app, a Python API, or a full-stack microservice, Docker gives you consistency, speed, and portability.

## Bonus: Quick Reference Sheet
```pgsql
docker build -t name .
docker run -p 8080:80 name
docker ps -a
docker exec -it container bash
docker-compose up -d
```
