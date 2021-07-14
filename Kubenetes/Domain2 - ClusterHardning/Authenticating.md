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

