# Setup the Kubernetes environment with Minikube

The instructions will work on Linux and macOS, they have not been tested on Windows.

The [Minikube Getting Started](https://minikube.sigs.k8s.io/docs/start/) has detailled instructions on how to install Minikube for the different platforms.

### Start a Minikube "cluster"

In this workshop we will use Minikube in a somewhat minimal configuration with 2 CPUs and 4 GB om memory. 

The Docker driver allows you to install Kubernetes into an existing Docker install. On Linux, this does not require any virtualization to be enabled, on macOS this is using the Docker Desktop virtualization environment (HyperKit). 

```
minikube start --cpus 2 --memory 4096 --driver=docker
```
