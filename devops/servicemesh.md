# Service Mesh

## What is a service mesh

A service mesh, like the open source project Istio, is a way to control how different parts of an application share data with one another. Unlike other systems for managing this communication, a service mesh is a dedicated infrastructure layer built right into an app.

Each part of an app, called a "service," relies on other services to give users what they want.

The logic governing communication can be coded into each service without a service mesh layer.


## How does it work?

A service mesh does not introduce new functionality to an app’s runtime environment.

What’s different about a service mesh is that it takes the logic governing service-to-service communication out of individual services and abstracts it to a layer of infrastructure.

In a service mesh, requests are routed between microservices through proxies in their own infrastructure layer. 

---

#ISTIO (Opensource tool to implement ServiceMesh)

Istio is an implementation of a service mesh. A service mesh is the connective tissue between your services that adds additional capabilities like traffic control, service discovery, load balancing, resilience, observability, security, and so on.

Istio is a Greek nautical term that means “sail”— much like Kubernetes itself is the Greek term for “helmsman” or “ship’s pilot”. With Istio, there has been an explosion of interest in the concept of the service mesh—where Kubernetes/OpenShift has left off is where Istio begins.

## Understanding ISTIO components

The Istio service mesh is primarily composed of two major areas:

- the data plane
- the control plane

## Data Plane

The Data Plane is implemented such a way that it interpretes all *ingress* and *egress* rules in network traffic.

Let explore each component of DataPlane

### Service Proxy

