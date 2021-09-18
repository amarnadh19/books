# Kubernetes Storage


Volumes are the basic identity used as storage in K8. Volumes can be persistent or non-persistent.

## How Does Kubernetes Storage Work?

### Volume

Volumes are basic storage in K8. They can be created through NFS or Local Storage or Cloud storage. Volumes can be accessed directly from Pods or Persistent Volume (PV). (PV is an object in K8)


### Non-Persistent Storage

By Default K8 storage is temporary. Any data stored in Containers is non persistent container storage is portable but not durable.


### Persistent Storage

Persistent storage models

	- Files
	- Block Storage
	- Object Storage
	- Cloud Storage

Storage can directly called within Pod but it voliates the pod Portability. Hence this method is not recommended. Instead need to use PV and PVCs

### Persistent Volume

Administrators define storage resouces, together with help of paramaters like Performance, Capacity required, Cost needed for the storage. These parameters are defined in Persistent volume.

PV's are not portable between cluster to cluster.


### Persistent Volume Claim (PVC)

To define the required storage by developers or users. These are portable can be moved with application


### Deployments and stateless sets

Deployments share the same PVC. This leads to stability issues. The better opition is to run pods as stateless sets, which allows you to clone PVCs between containers.


### Storage Class

Each storage class represents a type of storage. Tese storage class can be assigned to Persistent Volume.


## Kubernetes Storage Best Practices

Managing Kubernetes storage can be complex. The following best practices will help you manage storage more effectively.


### Persistent Volume Settings


- Always include a PVC in pod configuration.

- Never include a PV in the configuration (because this violates portability).

- Always create a default storage class.

- Give users the option to select a StorageClass in their PVC.


### Resource Quotas for Namespaces


Resource quotas are also available at the namespace level, giving you another layer of control over cluster resource usage.

Resource quotas limit the total amount of CPU, memory, and storage resources that can be used by all containers running in the namespace. 

It can also limit consumption of storage resources according to service levels or backup.

The following command checks if resource quotas are enabled at the namespace level:

```
kubectl describe namespace <namespace_name>

```

### Support High Performance with Quality of Service Definitions


Some Kubernetes providers extend the definition of a PVC with quality of service (QoS) parameters. This means it prioritizes read/write volumes for specific deployments, enabling higher throughput if needed by the application.


