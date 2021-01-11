# Workshop: Get started with security for your Java Microservices application

This workshop is an adaptation of the IBM Workshop [Get started with security for your Java Microservices application](https://ibm-developer.gitbook.io/get-started-with-security-for-your-java-microservi/).

The IBM Workshop uses preprovisioned Kubernetes clusters on the IBM Cloud based on IBM Cloud Kubernetes Service (IKS).

This version of the workshop is based on [Minikube](https://minikube.sigs.k8s.io/docs/) running on your own workstation.  

---

In this workshop you will learn how to get started with Application Security from two perspectives:
* Platform security
* Authentication and Authorization implementation

We will show you with an example application:
* How to secure external access to a Kubernetes cluster with TLS
* How to secure communication between Microservices with Istio and mTLS
* How to implement authorization and authentication with the Open Source Identity and Access Management system Keycloak and JSON Web Tokens (JWT)

The exercises are based on an example application based on our Open Source Github project [Cloud Native Starter](https://github.com/IBM/cloud-native-starter/tree/master/security), build with Quarkus and Microprofile

The following screenshot shows the web application, you have to logon to see the list of articles.

<kbd><img src="images/architecture-wep-app-screenshot.png"/></kbd>

### Architecture

The following diagram shows the architecture of the sample application. There is a Web-App service that serves the Javascript/Vue.js code to the browser. The Web-App code running in the browser invokes a REST API of the Web-API microservice. The Web-API microservice in turn invokes a REST API of the Articles microservice. 

To see the results in the web application, users need to be authenticated and they need to have the role `user`. 

<kbd><img src="images/architecture-diagram.png"/></kbd>

### Estimated time and level

|  Time | Level  |
| - | - |
| one hour | beginners |

### Objectives

After completion of this workshop, you should understand the following application security related topics:

**Application security provided by the platform**
* [TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security)/[HTTPS](https://en.wikipedia.org/wiki/HTTPS)
* [mTLS](https://en.wikipedia.org/wiki/Mutual_authentication)

**Application security with Keycloak and Quarkus**
* [Authentication with Keycloak](https://en.wikipedia.org/wiki/Authentication) on the Web Fronted
* [Authorization in Quarkus](https://en.wikipedia.org/wiki/Authorization) for specific Microservices in the backend

*The scope of this workshop is not to explain every aspect of application security.*

### Agenda

These are the sections of this workshop, go through all of them in sequence, start with `1. Setup the IBM Cloud Environment` :

 1. [Setup the Kubernetes Environment](pre-work/README.md) 
 2. [Setup the application environment](app-env-exercise-01/README.md) 
 3. [Platform security with mTLS](p-sec-exercise-01/README.md) 
 4. [Application security with Keycloak and Quarkus](app-sec-exercise-01/README.md) 

### Compatibility

This workshop has been tested on the following platforms:

* **Minikube**: Version 1.15.1 
* **Istio**: Version 1.8.1 


### Technology Used

* [Microservices architecture](https://en.wikipedia.org/wiki/Microservices)
* [Keycloak](https://www.keycloak.org)
* [Jakarta EE](https://jakarta.ee/)
* [MicroProfile](https://microprofile.io/)
* [Quarkus](https://quarkus.io/ingress)
* [Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/)
* [Istio](https://https://istio.io)
* [Vue.js](https://vuejs.org/)
* [git 2.24.1 or higher](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
* [yarn 1.22.4 or higher](https://yarnpkg.com)
* [Node.js v14.6.0 or higher](https://nodejs.org/en/)
* [Apache Maven 3.6.3](https://maven.apache.org/ref/3.6.3/maven-embedder/cli.html)

### Credits

* [Niklas Heidloff](https://twitter.com/nheidloff)
* [Harald Uebele](https://twitter.com/Harald_U)
* [Thomas Südbröcker](https://twitter.com/tsuedbroecker)

### Additional resources

[Here](workshop/BLOGS.md) are some blogs that describe how this project has been implemented-

The presentation that goes with this workshop is available [here](images/App-Security-Final-V1-20200821.pdf).
