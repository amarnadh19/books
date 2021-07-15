# Users in Kubernetes

All Kubernetes clusters have to categories of users: **service accounts managed by Kubernetes and Normal users**.

It is assumed that a cluster-independent service manages normal users in the following ways:

- an administrator distributing private keys
- a user store like Keystone or Google Accounts
- a file with a list of usernames and passwords

Kubernetes does not have objects which represent *normal user accounts*. Normal users cannot be added to a cluster through an API call.

Even though a normal user cannot be added via an API call, any user that presents a valid certificate signed by the cluster's certificate authority (CA) is considered authenticated

In contrast, service accounts are users managed by the Kubernetes API. They are bound to specific namespaces, and created automatically by the API server or manually through API calls. 

Service accounts are tied to a set of credentials stored as ```Secrets```, which are mounted into pods allowing in-cluster processes to talk to the Kubernetes API.

API requests are tied to either a normal user or a service account, or are treated as *anonymous requests*.

This means every process inside or outside the cluster, from a human user typing kubectl on a workstation, to kubelets on nodes, to members of the control plane, must authenticate when making requests to the API server, or be treated as an anonymous user.

## Authentication strategies

Kubernetes uses client certificates, bearer tokens, an authenticating proxy, or HTTP basic auth to authenticate API requests through authentication plugins.

As HTTP requests are made to the API server, plugins attempt to associate the following attributes with the request:

- Username: a string which identifies the end user. Common values might be kube-admin or jane@example.com.

- UID: a string which identifies the end user and attempts to be more consistent and unique than username.

- Groups: a set of strings, each of which indicates the user's membership in a named logical collection of users. Common values might be system:masters or devops-team.

- Extra fields: a map of strings to list of strings which holds additional information authorizers may find useful.

