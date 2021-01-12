# Setup the Kubernetes environment with Minikube

The instructions will work on Linux and macOS, they have not been tested on Windows.

The [Minikube Getting Started](https://minikube.sigs.k8s.io/docs/start/) has detailled instructions on how to install Minikube for the different platforms.

### Start a Minikube "cluster"

In this workshop we will use Minikube in a somewhat minimal configuration with 2 CPUs and 4 GB om memory. 

The Docker driver allows you to install Kubernetes into an existing Docker install. On Linux, this does not require any virtualization to be enabled, on macOS this is using the Docker Desktop virtualization environment (HyperKit). 

```
minikube start --cpus 2 --memory 4096 --driver=docker
```
Output:

```
😄  minikube v1.15.1 auf Linuxmint 20.1
✨  Using the docker driver based on user configuration
👍  Starting control plane node minikube in cluster minikube
🔥  Creating docker container (CPUs=2, Memory=4096MB) ...
🐳  Vorbereiten von Kubernetes v1.19.4 auf Docker 19.03.13...
🔎  Verifying Kubernetes components...
🌟  Enabled addons: storage-provisioner, default-storageclass
🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default

```

Initial start will take a moment.

The [Minikube Getting Started](https://minikube.sigs.k8s.io/docs/start/) has instructions on how to manage the Minikube cluster.

