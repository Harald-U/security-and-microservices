# Overview: Setup Istio and Keycloak

We need Keycloak for authentication and authorization. And we need Istio to secure access to our services. 

In the following exercises we will:

* Install Istio on Minikube.
* We will use the Istio Ingress gateway to gain access to our sample application and to Keycloak externally.
* We will secure the Istio Ingress gateway with HTTPS using a self-signed certificate.
* Install Keycloak within the Istio Service Mesh.
