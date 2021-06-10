# MANAGED IDENTITIES

## What are managed identities for Azure resources?
A common challenge for developers is the management of secrets and credentials used to secure communication between different components making up a solution. 

Managed identities eliminate the need for developers to manage credentials. 

Managed identities provide an identity for applications to use when connecting to resources that support Azure Active Directory (Azure AD) authentication. 

Applications may use the managed identity to obtain Azure AD tokens.

For example, an application may use a managed identity to access resources like **Azure Key Vault** where developers can store credentials in a secure manner or to access storage accounts.

Here are some of the benefits of using Managed identities:

- You don't need to manage credentials. Credentials are not even accessible to you.

- You can use managed identities to authenticate to any resource that supports Azure Active Directory authentication including your own applications.

- Managed identities can be used without any additional cost.

    Note:

    Managed identities for Azure resources is the new name for the service formerly known as Managed Service Identity (MSI).


## Managed identity types

There are two types of managed identities:

- **System-assigned** 

  - Some Azure services allow you to enable a managed identity directly on a service instance.

  - System-assigned Some Azure services allow you to enable a managed identity directly on a service instance.

  - So when the resource is deleted, Azure automatically deletes the identity for you.

- **User-assigned**

  - You can create a user-assigned managed identity and assign it to one or more instances of an Azure service. 
  
  - In the case of user-assigned managed identities, the identity is managed separately from the resources that use it.


![](https://github.com/amarnadh19/books/blob/main/images/az_managedidentities_1.png?)


    Note:

    Regardless of the type of identity chosen a managed identity is a service principal of a special type that may only be used with Azure resources. When the managed identity is deleted, the corresponding service principal is automatically removed.

Managed identities for Azure resources can be used to authenticate to services that support Azure AD authentication.


## Which operations can I perform using managed identities?

Resources that support system assigned managed identities allow you to:

- Enable or disable managed identities at the resource level.
- Use RBAC roles to grant permissions.
- View create, read, update, delete (CRUD) operations in Azure Activity logs.
- View sign-in activity in Azure AD sign-in logs.

If you choose a user assigned managed identity instead:

- You can create, read, update, delete the identities.
- You can use RBAC role assignments to grant permissions.
- User assigned managed identities can be used on more than one resource.
- CRUD operations are available for review in Azure Activity logs.
- View sign-in activity in Azure AD sign-in logs.

Operations on managed identities may be performed by using an Azure Resource Manager (ARM) template, the Azure Portal, the Azure CLI, PowerShell, and REST APIs.


## How Managed identity works

Internally, managed identities are service principals of a special type, which can only be used with Azure resources.

When a User-Assigned or System-Assigned Identity is created, the Managed Identity Resource Provider (MSRP) issues a certificate internally to that identity.

https://docs.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/managed-identity-best-practice-recommendations

