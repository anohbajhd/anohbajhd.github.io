+++
date = '2025-07-25T12:15:56+05:00'
title = "Modern Infrastructure – Part 2: Kubernetes"
description = "Container Orchestration: Local Cluster Setup Using Minikube"
tags = ['kubernetes', 'kubectl', 'minikube', 'cluster', 'container orchestration']
+++

## Introduction

In the evolving world of cloud-native applications, containerization has revolutionized how we build, ship, and run software. But as the number of containers in a project grows, managing them becomes a challenge. That’s where Container Orchestration steps in - and Kubernetes is the undisputed leader in this space.

## What is Container Orchestration?

Container orchestration is a way to automate the deployment, scaling, and management of many containers.

Instead of starting and stopping each container manually, orchestration tools (like Kubernetes) handle it for you - making sure your apps run smoothly, restart if they crash, and scale when needed.

It's like having a smart system that keeps all your containerized apps organized and running the way you want, across multiple machines.

## What Is Kubernetes?

**Kubernetes (K8s)** is an open-source platform that automates deploying, scaling, and managing containerized applications.

Originally built by Google and now maintained by the Cloud Native Computing Foundation (CNCF), it enables:

 - **Automatic container scheduling**

 -  **Load balancing**

 -  **Self-healing and auto-scaling**

 -  **Service discovery**

---
## Why Minikube and kubectl?

To run Kubernetes on your local machine, you need two key tools:

### 1. kubectl - The Kubernetes Command-Line Tool

`kubectl` is the primary way to interact with a Kubernetes cluster. You use it to:

  -  Deploy applications

  -  Inspect and manage cluster resources

  -  View logs

  -  Scale deployments

  -  Expose services

Without `kubectl`, you cannot communicate with your cluster’s API server or manage any workloads.

    Think of `kubectl` as your terminal interface to Kubernetes - just like git is to version control.

### 2. Minikube - Local Kubernetes Cluster

`Minikube` is a lightweight tool that sets up a single-node Kubernetes cluster on your machine. It’s ideal for:

  -  Learning Kubernetes basics

  -  Local development

  -  Testing configuration files before production
  
  ---

## Prerequisites

Make sure you have:

  -  A system with virtualization enabled (Docker, VirtualBox, etc.)

  -  Terminal access with sudo privileges

  -  Internet connection

## Step-by-Step Installation Guide (Ubuntu/Linux)

### Step 1: Install `kubectl`

1. Downlaod the latest stable version:
![command screenshot](/kubernetes/s1.png)

2. Then make the file executable with:
![command screenshot](/kubernetes/s2.png)

3. Move it to your system's binary path by: 
![command screenshot](/kubernetes/s3.png)

4. Check the version if it is installed successfully:
![command screenshot](/kubernetes/s4.png)

---
### Step 2: Install `minikube`

1. Downloa the minikube binary:
![command screenshot](/kubernetes/s5.png)

2. Install it to your system path:
![command screenshot](/kubernetes/s6.png)

3. Check version:
![command screenshot](/kubernetes/s7.png)

### Step 3: Start the Kubernetes Cluster

1. **Recommended:** Choose a driver (Docker is common): 
![command screenshot](/kubernetes/s8.png)

2. **Optional:** this command automatically selects the best available driver on your system (e.g., Docker, VirtualBox, KVM):
![command screenshot](/kubernetes/s9.png)

This downloads the required components and spins up a single-node cluster.

---


### Step 4: Verify the Cluster is Running

![command screenshot](/kubernetes/s10.png)

### Step 5: Interact with Your Cluster

![command screenshot](/kubernetes/s11.png)

You should see one node in a Ready state.

---
### Step 6: Deploy a Sample App
#### Do you have a deployment?
![command screenshot](/kubernetes/sz.png)

#### If there’s no output, create one:

#### Option 1:
Through kubernetes CLI (kubectl):
```bash
kubectl create deployment hello-node --image=k8s.gcr.io/echoserver:1.4
```

#### Option 2:
 Using the Kubernetes Dashboard (Optional UI):

1. Lanch the minikube dashboard:
![command screenshot](/kubernetes/sa.png)

2. If the output says somethin like:
```bash
No resources found in kubernetes-dashboard namespace.
```

It means the dashboard pods haven’t been created yet - so naturally, proxy health will hang since there's nothing to proxy to.

---
### How to Fix it: Manually Enable the Dashboard Addon

Minikube is supposed to auto-enable it with minikube dashboard, but sometimes it silently fails. You can force it like this:
![command screenshot](/kubernetes/sb.png)

Then manually install the metrics scraper (recommended for full functionality):
![command screenshot](/kubernetes/sc.png)

#### Wait and Watch:
Then watch pods getting created:
![command screenshot](/kubernetes/sd.png)

#### Once Running:

Launch the dashboard again:
```bash
minikube dashboard
```

![command screenshot](/kubernetes/sx.png)

 Boom! You're in the Kubernetes Dashboard - mission accomplished!
This means your entire Minikube cluster is working exactly as it should.

----

### What You Can Do From Here

Now that you're inside the dashboard UI, here are a few things worth exploring:
 #### 1. Workloads

   - Check out: Deployments, Pods, ReplicaSets

   - Try creating a sample deployment from the UI

 #### 2. Create a Deployment

Use the "+" button (top-right) or go to:

   - `+` CREATE → Deploy a containerized app

I did this simple yaml:
   ```yaml
   apiVersion: apps/v1
kind: Deployment
metadata:
  name: hello-node
spec:
  replicas: 1
  selector:
    matchLabels:
      app: hello
  template:
    metadata:
      labels:
        app: hello
    spec:
      containers:
      - name: hello
        image: k8s.gcr.io/echoserver:1.10
        ports:
        - containerPort: 8080
```

 #### 3. Expose a Service

You can expose your deployment right from the dashboard as a NodePort 
![command screenshot](/kubernetes/sy.png)

-then open it in a browser using:
![command screenshot](/kubernetes/se.png)

This will:

   - Create a Service named hello-node

   - Expose port 8080 of your pod

   - Assign a random NodePort between 30000–32767

---


#### To access the app:
![command screenshot](/kubernetes/sg.png)

It should open in your browser!
![command screenshot](/kubernetes/sh.png)

---

### Stopping or Cleaning Up

1. When you're done, you can stop the cluster:
```bash
minikube stop
```
2. To delete the cluster entirely:
```bash
minikube delete
```
---

## Conclusion

Kubernetes might seem complex at first, but starting with a local setup helps demystify it. By running a cluster on your own machine using Minikube, you gain the confidence to move to production environments later.

Kubernetes isn’t just a tool - it’s a platform that empowers you to build resilient, scalable, and manageable applications at scale.

  `  "Learning Kubernetes is like learning how to drive a spaceship. But once you do, you're ready to explore galaxies."`

----

## Commands List
```bash
curl -LO "https://dl.k8s.io/release/$(curl -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

chmod +x kubectl

sudo mv kubectl /usr/local/bin/
____________________________________________________________________________________________________________
   
kubectl version --client

curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

sudo install minikube-linux-amd64 /usr/local/bin/minikube

minikube version

minikube start --driver=docker

minikube status
____________________________________________________________________________________________________________

kubectl get nodes

minikube dashboard
##or
minikube dashboard --url

kubectl create deployment hello-node --image=k8s.gcr.io/echoserver:1.4

minikube addons enable dashboard

minikube addons enable metrics-server
____________________________________________________________________________________________________________

kubectl get pods -n kubernetes-dashboard -w

kubectl expose deployment hello-node --type=LoadBalancer --port=8080

kubectl get service hello-node

minikube service hello-node


```