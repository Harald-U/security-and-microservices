# 1 - Setup the work environment with Minikube

The instructions will work on Linux and macOS, they have not been tested on Windows bt should work, too.

The [Minikube Getting Started](https://minikube.sigs.k8s.io/docs/start/){:target="_blank"} has detailled instructions on how to install Minikube for the different platforms.

### Step 1: Download the code from this repository

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
Output:

```
😄  minikube v1.16.0 on Linuxmint 20.1
✨  Using the docker driver based on user configuration
👍  Starting control plane node minikube in cluster minikube
🚜  Pulling base image ...
💾  Downloading Kubernetes v1.20.0 preload ...
    > preloaded-images-k8s-v8-v1....: 491.00 MiB / 491.00 MiB  100.00% 3.41 MiB
🔥  Creating docker container (CPUs=2, Memory=4096MB) ...
🐳  Preparing Kubernetes v1.20.0 on Docker 20.10.0 ...
    ▪ Generating certificates and keys ...
    ▪ Booting up control plane ...
    ▪ Configuring RBAC rules ...
🔎  Verifying Kubernetes components...
🌟  Enabled addons: storage-provisioner, default-storageclass
🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
```

Initial start will take a while because it downloads the Kubernetes preload image. 

The [Minikube Getting Started](https://minikube.sigs.k8s.io/docs/start/) has instructions on how to manage the Minikube cluster.

---

**Continue with** [2 - Setup Istio](../02-app-env-exercise/SETUP_ISTIO.md)