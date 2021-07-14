# Controlling access to the Kubernetes

Users access the kubernetes APi using *kubectl*, client libraries or by making REST requests.

Both human users and K8 service accounts can be authorized for API access.

    Note:

    Service account:

    A service account provides an identity for processes that run in a pod when you create a pod, if you do not specify a service account, it is automatically assigned the default service account in the same NameService.

When a request reaches the API, it goes through several stages, illustrated in the following diagram:

![](https://github.com/amarnadh19/books/blob/main/images/cks_domain2_1.png?)

## Transport security

In a typical K8 cluster, the API servers on port 443, Protected by TLS. 

The API Server presents a certificate. This certificate may be signed using a private certificate  or based on a public key infrastructure linked to a generally recognized CA.

If your cluster uses a private certificate authority, you need a copy of that CA certificate configured into your ```~/.kube/config```

## Authentication

Once TLS is established the HTTP request moves to the authentication App.

This is shown as step 1 in the diagram

The Cluster creation script or Cluster admin configures the API server to run one or more authentication module.

The input to authentication step includes client certificate.

Authentication modules include client certificates, password, and plain tokens, bootstrap tokens, and JSON Web Tokens (used for service accounts).

Multiple authentication modules can be specified, in which case each one is tried in sequence, until one of them succeeds.

If the request coannot be authenciated,  it is rejected with HTTP status code 401. 


## Authorization

After user got authenticated, we need authorization to access resources.

Below example give User: amar; only access to read pod in namespace testing.

```

{
    "apiVersion": "abac.authorization.kubernetes.io/v1beta1",
    "kind": "Policy",
    "spec": {
        "user": "bob",
        "namespace": "projectCaribou",
        "resource": "pods",
        "readonly": true
    }
}

```

Kubernetes supports multiple authorization modules, such as ABAC mode, RBAC Mode, and Webhook mode. When an administrator creates a cluster, they configure the authorization modules that should be used in the API server. If more than one authorization modules are configured, Kubernetes checks each module, and if any module authorizes the request, then the request can proceed. If all of the modules deny the request, then the request is denied (HTTP status code 403).

## Admission control

Admission Control modules are software modules that can modify or reject requests. In addition to the attributes available to Authorization modules, Admission Control modules can access the contents of the object that is being created or modified. 

Unlike Authentication and Authorization modules, if any admission controller module rejects, then the request is immediately rejected.


## API server ports and IPs

The API server can actually serve on 2 ports:

By default the Kubernetes API server serves HTTP on 2 ports:

1. localhost port:
   - is intended for testing and bootstrap and for other components of the master node (scheduler, controller-manager) to talk to the API.
   - No TLS
   - default is port 8080, change with --insecure-port flag.
   - default IP is localhost, change with --insecure-bind-address flag
   - request bypasses authentication and authorization modules.
   - protected by need to have host access.
2. "SecurePort":
   - use whenever possible
   - uses TLS. Set cert with --tls-cert-file and key with --tls-private-key-file flag.
   - default is port 6443, change with --secure-port flag.
   - default IP is first non-localhost network interface, change with --bind-address flag.
   - request handled by authentication and authorization modules.
   - authentication and authorization modules run.
