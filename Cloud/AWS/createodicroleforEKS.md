# Create an IAM OIDC provider for your cluster


Your cluster has an OpenID Connect issuer URL associated with it. To use IAM roles for service accounts, an IAM OIDC provider must exist for your cluster.


## Prerequisites

An existing cluster. If you don't have one, you can create one using one of the Getting started with Amazon EKS guides.


**To create an IAM OIDC identity provider for your cluster with eksctl**


1) Determine whether you have an existing IAM OIDC provider for your cluster.


   View your cluster's OIDC provider URL.

```aws eks describe-cluster --name <cluster_name> --query "cluster.identity.oidc.issuer" --output text```


**Example output:**

```https://oidc.eks.us-west-2.amazonaws.com/id/EXAMPLED539D4633E53DE1B716D3041E```


List the IAM OIDC providers in your account. Replace <EXAMPLED539D4633E53DE1B716D3041E> (including <>) with the value returned from the previous command.

```aws iam list-open-id-connect-providers | grep <EXAMPLED539D4633E53DE1B716D3041E>```


**Example output**

```"Arn": "arn:aws-cn:iam::111122223333:oidc-provider/oidc.eks.us-west-2.amazonaws.com/id/EXAMPLED539D4633E53DE1B716D3041E"```


If output is returned from the previous command, then you already have a provider for your cluster. If no output is returned, then you must create an IAM OIDC provider.

Create an IAM OIDC identity provider for your cluster with the following command. Replace <cluster_name> (including <>) with your own value.

```eksctl utils associate-iam-oidc-provider --cluster <cluster_name> --approve```