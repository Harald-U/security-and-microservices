# Overview: Setup Istio and Keycloak

We need Istio to secure access to our services. And we need Keycloak for authentication and authorization. 

In the following exercises we will:

* Install Istio on Minikube.
* We will use the Istio Ingress gateway to gain access to our sample application and to Keycloak externally.
* We will secure the Istio Ingress gateway with HTTPS using a self-signed certificate.
* Install Keycloak within the Istio Service Mesh.

---

# 2 - Setup Istio

### Step 1: Download Istio

Note: The workshop has been tested with and is written for Istio 1.8.1. 

Go to the [Istio release page](https://github.com/istio/istio/releases/tag/1.8.1) to download the installation file for your OS, or download and extract the latest release automatically (Linux or macOS):

```
curl -L https://istio.io/downloadIstio | ISTIO_VERSION=1.8.1 sh -
```

Output:

```
Istio 1.8.1 Download Complete!

Istio has been successfully downloaded into the istio-1.8.1 folder on your system.

Next Steps:
See https://istio.io/latest/docs/setup/install/ to add Istio to your Kubernetes cluster.

To configure the istioctl client tool for your workstation,
add the /home/harald/temp/test/istio-1.8.1/bin directory to your environment path variable with:
	 export PATH="$PATH:/home/harald/temp/security-and-microservices/deployments/istio-1.8.1/bin"
Begin the Istio pre-installation check by running:
	 istioctl x precheck 
```

The installation directory contains:
* Sample applications in samples/
* The istioctl client binary in the bin/ directory.

Add the istioctl client to your path using the command from the Istio installations output, e.g.:

```
export PATH="$PATH:/home/harald/temp/security-and-microservices/deployments/istio-1.8.1/bin"
```

**Note:** Copy this PATH statement somewhere as you may need it later!

Test with

```
istioctl version
```

Output:

```
no running Istio pods in "istio-system"
1.8.1
```

The output indicates that Istio is not installed in our Kubernetes cluster and that `istioctl` is of version 1.8.1.

### Step 2: Setup Istio with an operator 

The following commands will install the Istio operator, create a namespace for the Istio backplane, and start to installation of the Istio backplane.

1. Operator

	```sh
	istioctl operator init
	```

1. Namespace

	```sh
	kubectl create ns istio-system
	```

1.  Istio deployment

	```sh
	kubectl apply -f istio.yaml
	```

1. Label 'default' namespace for Istio pod auto-injection

	```sh
	kubectl label namespace default istio-injection=enabled
	```

### Step 3: Check the status of Istio deployment

```sh
kubectl get pod -n istio-system
```

When deployment is complete the result should look like this:

```sh
NAME                                    READY   STATUS    RESTARTS   AGE
istio-egressgateway-d84f95b69-b222c     1/1     Running   0          32s
istio-ingressgateway-75f6d79f48-bqhhb   1/1     Running   0          32s
istiod-7c67c6b6c8-dskz6                 1/1     Running   0          49s
```

### Step 4: Install Kiali

[Kiali](https://kiali.io/) is an observability console for Istio with service mesh configuration and validation capabilities. It helps you understand the structure and health of your service mesh by monitoring traffic flow to infer the topology and report errors. 

In earlier versions of Istio, Kiali and the other telemetry services have been installed by default. This is no longer true with Istio 1.8. Detailled instructions can be found in the [Integrations](https://istio.io/latest/docs/ops/integrations/) section of the Istio documentation.

Kiali requires Prometheus:

```
kubectl apply -f istio-1.8.1/samples/addons/prometheus.yaml
```

This will install Prometheus into the istio-system namespace.
This assumes that Istio 1.8.1 was downloaded. You may need to adjust the path accordingly.

To install Kiali, you need to execute this command **twice**:

```
kubectl apply -f istio-1.8.1/samples/addons/kiali.yaml
```

The first execution of the command will throw errors about not finding a match for kind "MonitoringDashboard". This is expected: The kiali.yaml file creates a Custom Resource Definition (CRD) of kind "MonitoringDashboard" and this takes a moment.

The second execution of the command should run without errors.

Check with 

```sh
kubectl get pod -n istio-system
```

When deployment is complete the result should look like this:

```sh
istio-egressgateway-d84f95b69-b222c     1/1     Running   0          10m
istio-ingressgateway-75f6d79f48-bqhhb   1/1     Running   0          10m
istiod-7c67c6b6c8-dskz6                 1/1     Running   0          10m
kiali-7476977cf9-vfxtm                  1/1     Running   0          3m28s
prometheus-7bfddb8dbf-fvt87             2/2     Running   0          49s
```

---

**Continue with** [3 - Expose the Istio Ingress gateway via HTTPS/TLS](./SETUP_ISTIO_INGRESS.md)