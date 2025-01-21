---
title: 2 - Setup Istio
layout: default
---

# Overview: Setup Istio and Keycloak

We need Istio to secure access to our services. And we need Keycloak for authentication and authorization. 

In the following exercises we will:

* Install Istio on Minikube.
* We will use the Istio Ingress gateway to gain access to our sample application and to Keycloak externally.
* We will secure the Istio Ingress gateway with HTTPS using a self-signed certificate.
* Install Keycloak within the Istio Service Mesh.

---

# 2 - Setup Istio

### Step 1: Download and Install Istio

Note: The workshop has been tested with and is written for Istio 1.24.2. 

Note 2: If you completed the **Istio Handson** workshop recently or if you are running this workshop on bwLehrpool, you should have downloaded Istio 1.24.2 already, skip to **2. Install Istio** then.  

1. Get the Istio code:

	```
	curl -L https://istio.io/downloadIstio | ISTIO_VERSION=1.24.2 TARGET_ARCH=x86_64  sh -
	```

2. Install Istio:

    ```
	istio-1.24.2/bin/istioctl install --set profile=demo -y
    ```

	**On bwLehrpool** use this command instead:

	```
	/home/student/istio-1.24.2/bin/istioctl install --set profile=demo -y
	```


### Step 2: Check the status of Istio deployment

```sh
kubectl get pod -n istio-system
```

When the deployment is complete the result should look like this:

```sh
NAME                                    READY   STATUS    RESTARTS   AGE
istio-egressgateway-d84f95b69-b222c     1/1     Running   0          32s
istio-ingressgateway-75f6d79f48-bqhhb   1/1     Running   0          32s
istiod-7c67c6b6c8-dskz6                 1/1     Running   0          49s
```

### Step 3: Enable automatic sidecar injection

This command enables automatic sidecar injection for the `default` namespace:

```
kubectl label namespace default istio-injection=enabled	
```

> Without this setting we will not use Istio although it is installed! 


### Step 4: Install Kiali

[Kiali](https://kiali.io/){:target="_blank"} is an observability console for Istio with service mesh configuration and validation capabilities. It helps you understand the structure and health of your service mesh by monitoring traffic flow to infer the topology and report errors. 

In earlier versions of Istio, Kiali and the other telemetry services have been installed by default. This is no longer true with newer versions. Detailled instructions can be found in the [Integrations](https://istio.io/latest/docs/ops/integrations/){:target="_blank"} section of the Istio documentation.

Kiali requires Prometheus:

```
kubectl apply -f istio-1.24.2/samples/addons/prometheus.yaml
```

**On bwLehrpool** use this command instead:

```
kubectl apply -f /home/student/istio-1.24.2/samples/addons/prometheus.yaml
```

This will install Prometheus into the istio-system namespace.
This assumes that Istio 1.24.2 was downloaded. You may need to adjust the path accordingly.

To install Kiali, you need to execute this command:

```
kubectl apply -f istio-1.24.2/samples/addons/kiali.yaml
```

**On bwLehrpool** use this command instead:

```
kubectl apply -f /home/student/istio-1.24.2/samples/addons/kiali.yaml
```

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