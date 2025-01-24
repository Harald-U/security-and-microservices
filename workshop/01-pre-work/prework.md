---
title: 1 - Setup the work environment
layout: default
---

# 1 - Setup the work environment with Minikube

The instructions will work on Linux and macOS, they have not been tested on Windows but should work, too.

The [Minikube Getting Started](https://minikube.sigs.k8s.io/docs/start/){:target="_blank"} has detailled instructions on how to install Minikube for the different platforms. This workshop has been tested with Minikube version 1.35.0.

### Step 1: Download the code from this repository

On **bwLehrpool** change into the PERSISTENT directory, first!

```
git clone https://github.com/Harald-U/security-and-microservices.git
cd security-and-microservices/deployments/
```

### Step 2: Start a Minikube "cluster"

In this workshop we will use Minikube in a somewhat minimal configuration with 2 CPUs and 4 GB of memory. 

The Docker driver allows you to install Kubernetes into an existing Docker install. On Linux, this does not require any virtualization at all, on macOS this is using the virtualization of Docker Desktop (HyperKit). 

```
minikube start --cpus 2 --memory 4096 --driver=docker
```

### Step 2: Start a Minikube "cluster" on bwLehrpool

bwLehrpool has sufficient RAM to increase memory for Minikube, you can use this command instead:

```
minikube start --cpus 2 --memory 6144 --driver docker
```

which will assign 6 GB of RAM.

---

**Continue with** [2 - Setup Istio](../02-app-env-exercise/SETUP_ISTIO.md)