# Kubernetes Architecture in depth

Kubernetes was found in 2014 from google.

## Architecture of master node

A master node hosts the Kubernetes Control Plane, a set of services that administrate and orchestrate the whole cluster. These services run as pods in the "kube-system" namespace.


### API Server

The API server is the central part of the Kubernetes Control Plane, it is a REST API which is the entrypoint to issue commands to the cluster. This is what you interact with when you write `kubectl` commands. It communicates with the different components of the master and the worker nodes to apply the user-desired state.

API server’s persistent state is stored in a database that is external to the API server, the server itself is stateless and can be replicated to handle request load and for fault tolerance.

The main implementation of a Kubernetes API server is kube-apiserver. kube-apiserver is designed to scale horizontally—that is, it scales by deploying more instances. You can run several instances of kube-apiserver and balance traffic between those instances.


### ETCD

Consistent and highly-available key value store used as Kubernetes' backing store for all cluster data.

This is also where credentials required to authenticate the requests you send to the API are stored. In order to have a resilient Kubernetes cluster, there should be at least *3 ETCD instances*.


### kube-scheduler

The scheduler monitors the available resources on the different worker nodes and schedules pods and other Kubernetes resources to nodes in consideration of this. The scheduler ensures the workload is evenly balanced across the cluster.


### kube-controller-manager

The Controller Manager handles cluster orchestration. It oversees nodes leaving and joining the cluster and ensures the current state of the cluster is always in check with the desired state stored in ETCD. In case of a node failure, it will spin up new pods on the remaining nodes to match the wanted replica count.

Logically, each controller is a separate process, but to reduce complexity, they are all compiled into a single binary and run in a single process.

Some types of these controllers are:

- **Node controller**: Responsible for noticing and responding when nodes go down.
- **Job controller**: Watches for Job objects that represent one-off tasks, then creates Pods to run those tasks to completion.
- **Endpoints controller**: Populates the Endpoints object (that is, joins Services & Pods).
- **Service Account & Token controllers**: Create default accounts and API access tokens for new namespaces


### cloud-controller-manager

A Kubernetes control plane component that embeds cloud-specific control logic. The cloud-controller-manager only runs controllers that are specific to your cloud provider. If you are running Kubernetes on your own premises, or in a learning environment inside your own PC, the cluster does not have a cloud controller manager.

As with the kube-controller-manager, the cloud-controller-manager combines several logically independent control loops into a single binary that you run as a single process. You can scale horizontally (run more than one copy) to improve performance or to help tolerate failures.

The following controllers can have cloud provider dependencies:

- **Node controller**: For checking the cloud provider to determine if a node has been deleted in the cloud after it stops responding
- **Route controller**: For setting up routes in the underlying cloud infrastructure
- **Service controller**: For creating, updating and deleting cloud provider load balancers


## Node Components

Node components run on every node, maintaining running pods and providing the Kubernetes runtime environment.

### kubelet

An agent that runs on each node in the cluster. It makes sure that containers are running in a Pod.

The kubelet takes a set of PodSpecs that are provided through various mechanisms and ensures that the containers described in those PodSpecs are running and healthy. The kubelet doesn't manage containers which were not created by Kubernetes.

Kubelet communicates with the API and applies the resources configuration on the node. It also reports to the master the health of the node. 


### kube-proxy

kube-proxy is a network proxy that runs on each node in your cluster, implementing part of the Kubernetes Service concept.

kube-proxy maintains network rules on nodes. These network rules allow network communication to your Pods from network sessions inside or outside of your cluster.

kube-proxy uses the operating system packet filtering layer if there is one and it's available. Otherwise, kube-proxy forwards the traffic itself.

The Kubernetes Service Proxy acts as a load balancer. It routes network traffic and forwards services to expose them outside of the cluster.


### Container runtime

The container runtime is the software that is responsible for running containers.

Kubernetes supports several container runtimes: Docker, containerd, CRI-O, and any implementation of the Kubernetes CRI (Container Runtime Interface).


#### CRI (Container Runtime Interface)

CRI (Container Runtime Interface) consists of a specifications/requirements (to-be-added), protobuf API, and libraries for container runtimes to integrate with kubelet on a node. The CRI API is currently in Alpha, and the CRI-Docker integration is used by default as of Kubernetes 1.7+.

Below CRI available in market

- cri-o
- rktlet
- frakti
- cri-containerd
- singularity-cri


### Kube DNS

The Kubernetes DNS Service allow pods to communicate with each other using their name or FQDN (Fully Qualified Domain Name) instead of their local IP.


### Container Network Interface

The CNI creates virtual networks across the whole cluster to allow containers and pods to communicate regardless of what node they run on. It yields pods virtual network interfaces and local IP addresses.

![](https://github.com/amarnadh19/books/blob/main/images/k8_arch.png?)


***


# What happens when you deploy an app?

--> You send the description of your application and its configuration to the API on the master node through the `kubectl` command line utility. 

--> The API will store this configuration in the ETCD, and the Sheduler will assign your application pods to worker nodes.

--> On the worker nodes, Kubelet will receive the description of its scheduled pods and will notify the container runtime to run them.

-->  Kube proxy, the container network interface and kube DNS will then ensure that the created pods have network access and can communicate with other pods on the node and in the cluster.

--> If a pod fails, it may be rescheduled on any worker node following the same procedure.

![](https://github.com/amarnadh19/books/blob/main/images/k8_pod_creation.png?)


***

# Kubernetes Scheduler

## Scheduling overview

A scheduler watches for newly created Pods that have no Node assigned. 

For every Pod that the scheduler discovers, the scheduler becomes responsible for finding the best Node for that Pod to run on. The scheduler reaches this placement decision taking into account the scheduling principles

## kube-scheduler

kube-scheduler is the default scheduler for Kubernetes and runs as part of the control plane. kube-scheduler is designed so that, you can write your own scheduling component and use that instead.

In a cluster, Nodes that meet the scheduling requirements for a Pod are called *feasible nodes*. If none of the nodes are suitable, the pod remains unscheduled until the scheduler is able to place it.

Once a feasible node is selected, then scheduler notifies the API server about this decision in a process called *binding*.

