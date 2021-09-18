# Introducing Container Runtime Interface (CRI) in Kubernetes

At the lowest layers of a Kubernetes node is the software that, among other things, starts and stops containers. We call this the *“Container Runtime”*. The most widely known container runtime is *Docker*, but it is not alone in this space. 

In fact, the container runtime space has been rapidly evolving. As part of the effort to make Kubernetes more extensible, we've been working on a new plugin API for container runtimes in Kubernetes, called "CRI".


## What is the CRI and why does Kubernetes need it?

