# Using RBAC authorization

Role-based access control (RBAC) is a method of regulating access to computer or network resources based on the roles of individual users within your organization.

RBAC authorization uses the ``` rbac.authorization.k8s.io ``` API group to drive authorization decisions, allows you to dynamically configure policies through the KUBERNETES API.

To enable RBAC, start the API server with the ```---authorization-mode``` flag set to a comma-seperated list that includes RBAC; for example:

```
kube-apiserver --authorization-mode-Example, RBAC --other-options --more-options
```

## API objects

The RBAC API declares four kinds of Kubernetes object:

- Role
- ClusterRole
- RoleBinding
- ClusterRoleBinding.

### Role and Cluster Role

An RBAC *role* and *ClusterRole* contains rules that represents a set of permissions. Permissions are purely additive. No deny rule.

A Role always sets permissions within a particular namespace. When you create a Role, you have to specify the namespace it belongs in.

ClusterRole is non namespace resource. ClusterRoles have several uses. You can use a ClusterRole to:

- define permissions on namespace resources and be granted within individual namespace.
- define permissions on namespaced resources and be granted across all namespaces.
- define permissions on cluster-scoped resources.

**Role example **

```
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadadta:
  namespace: default
  name: pod-reader
rules:
  - apiGroups:[""]
    resouces: ["pods"]
    verbs: ["get","watch", "list"]
```

**Cluster Role example**

A clusterRole can be used to grant the same permissions as a Role. Because ClusterRoles are cluster-scoped

Grant access to:

- cluster-scoped resources (like nodes).
- non-resource endpoints (like /healthz)
- namespaced resources (like Pods), across all namespaces

For example you can use a clusterRole to allow a particular user to run ```kubectl get pods --all-namespaces```

Exampleof a ClusterRole that can be used to grant read access to secrets in any particualr namespace.
```
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  name: secret-reader

rules:
  - apiGroups: [""]
    resources: ["secrets"]
    verbs: ["get", "watch", "list"]
```

### RoleBinding and ClusterRoleBinding

A role binding grants the permissions defined in a role to a user or set of users. 

It holds a list of *subjects* (users, groups or service accounts) and a reference to the role being granted.

*RoleBinding* is namespace scope
*ClusterBinding* is cluster level scope

### Path Segments names

Resource names cannot use . or .. or / or %. This is called path segment name conversion.

**RoleBindings example**

```
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: Read-pods
  namespace: default
  
subjects:
  - kind : User
    name: jane
    apiGroup: rbac.authorizations.k8s.io
roleRef:
  kind: Role
  name: pod-reader
  apiGroup: rbac.authorization.k8s.io
```

**ClusterRoleBinding example**

```
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: read-secrets-global

subjects:
  - kind: Group
    name: manager
    apiGroup: rbac.authorization.k8s.io
    
roleRef:
  kind: ClusterRole
  name: secret-reader
  apiGroup: rbac.authorization.k8s.io
```

*After you create a binding, you cannot change the Role or clusterRole that it refers to.*

### Referring to resources

Pods is the namespaced resource for Pod resource and log is the subresource of pods. To represent this in an RBAC role, use (/) to delimit the resource and subresource.

```
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  namespace: default
  name: pod-and-pod-logs-reader
rules:
  - apiGroups: [""]
    resources: ["pods","pods/log"]
    verbs: ["get","list"]
```

You can also refer to resources by name for certain requests through the ```resourceNames```

```
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  namespace: default
  name: configmap-updater
  
rules:
  - apiGroups: [""]
    resources: ["configmaps"]
    resourceName: ["my-configmap"]
    verbs: ["update", "get"]
```

### Aggregated ClusterRoles

You can aggregate several clusterRoles into one combined ClusterRole.

example:

```
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  name: monitoring

aggregationRule:
  clusterRolesSelectors:
    - matchLabels:
      rbac.example.com/aggregate-to-monitoring: "true"
rules: []
```

Create a clusterrole which add to Aggregated ClusterRole

```
apiVersion: rbac.authorization.k8s,io/v1
kind: ClusterRole
metadata:
  name: montiroing-endpoints
  labels:
    rbac.example.com/aggregate-to-monitoring: "true"
rules:
  - apiGroups: [""]"
    resources: ["services", "endpoints","pods"]
    verbs: ["get","list","watch"]
```

The default user-facing roles use ClusterRole aggregation. 