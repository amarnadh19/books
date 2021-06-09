# Azure RBAC

## What is Azure role-based access control (Azure RBAC)?

*Role-based access control (RBAC) offers a slightly different approach*. 

Roles are defined as collections of access permissions. 

Azure RBAC is an authorization system built on Azure Resource Manager that provides fine-grained access management of Azure resources.


## What can I do with Azure RBAC?

Here are some examples of what you can do with Azure RBAC:

- Allow one user to manage virtual machines in a subscription and another user to manage virtual networks

- Allow a DBA group to manage SQL databases in a subscription

- Allow a user to manage all resources in a resource group, such as virtual machines, websites, and subnets

- Allow an application to access all resources in a resource group


## How Azure RBAC works

The way you control access to resources using Azure RBAC is to assign Azure roles.

This is key concept to understand - it is how permissions are enforced.

A role assignment consists of three elements: 
 - *Security principal* 
 - *role definition* and 
 - *scope*.


### Security principal

A *security principal* is an object that represents a user, group, service principal, or managed identity that is requesting access to Azure resources. 

You can assign a role to any of these security principals.

![](https://github.com/amarnadh19/books/blob/main/images/az_rbac_1.png?)


### Role definition

A *role definition* is a collection of permissions. 

It is typically just called a *role*. 

A role definition lists the operations that can be performed, such as *read, write* and *delete*. 

Roles can be high-level, like owner, or specific, like virtual machine reader.

![](https://github.com/amarnadh19/books/blob/main/images/az_rbac_2.png?)

Azure includes several Built-in-roles that you can use.

For example: Virtual Machine Contributor role allows a user to create and manage virtual machines.

If the build-in roles don't meet the specific needs of your organization, you can create your own *Azure Custom Roles*.


### Scope

*Scope* is the set of resources that the access applies to.

When you assign a role, you can further limit the actions allowed by defining a scope.

In Azure, you can specify a scope at four levels:

  - Management group
  - subscription
  - resource group
  - resource

Scopes are structured in a parent-child relationship. You can assign roles at any of these levels of scope.

![](https://github.com/amarnadh19/books/blob/main/images/az_rbac_3.png?)


### Role assignments

A *role assignment* is the process of attaching a role definition to a user, group, service principal, or managed identity at a particular scope for the burpose of granting access.

Access is granted by creating a role assignment, and access is revoked by removing a role assignment.

In this example, the Marketing group has been assigned the Contributor role for the pharma-sales resource group. This means that users in the Marketing group can create or manage any Azure resource in the pharma-sales resource group. Marketing users do not have access to resources outside the pharma-sales resource group, unless they are part of another role assignment.

![](https://github.com/amarnadh19/books/blob/main/images/az_rbac_4.png?)

You can assign roles using the Azure portal, Azure CLI, Azure PowerShell, Azure SDKs, or REST APIs.


## Groups

Role assignments are transitive for groups, which means that if a user is a member of a group and that group is a member of another group that has a role assignment, the will have the permissions in the role assignment.

![](https://github.com/amarnadh19/books/blob/main/images/az_rbac_5.png?)



## Multiple role assignments

So what happens if you have multiple overlapping role assignments? 

Azure RBAC is an additive model, so your effective permissions are the **sum of your role assignments**.

Consider the following example where a user is granted the Contributor role at the subscription scope and the Reader role on a resource group. The sum of the Contributor permissions and the Reader permissions is effectively the Contributor role for the subscription. Therefore, in this case, the Reader role assignment has no impact.

![](https://github.com/amarnadh19/books/blob/main/images/az_rbac_6.png?)


## Deny assignments

Previously, Azure RBAC was an allow-only model with no deny, but now Azure RBAC supports deny assignments in a limited way.

A role assignment defines a set of actions that are *allowed*, while a deny assignment defines a set of actions that are *not allowed*.

Similar to a role assignment, a *deny assignment* attaches a set of deny actions to a *user, group, service principal, or managed identity* at a particular scope for the purpose of denying access.

Deny assignments are created and managed by Azure to protect resources. 


## How Azure RBAC determines if a user has access to a resource

High level steps

1) A user (or service principal) acquires a token for Azure Resource Manager.

   The token includes the user's group memberships (including transitive group memberships).

2) The user makes a REST API call to Azure Resource Manager with the token attached.

3) Azure Resource Manager retrieves all the role assignments and deny assignments that apply to the resource upon which the action is being taken.

4) If a deny assignment applies, access is blocked. Otherwise, evaluation continues.

5) Azure Resource Manager narrows the role assignments that apply to this user or their group and determines what roles the user has for this resource.

6) Azure Resource Manager determines if the action in the API call is included in the roles the user has for this resource. 
   If the roles include Actions that have a wildcard *(*)*, the effective permissions are computed by subtracting the ```NotActions``` from the allowed ```Actions```. Similarly, the same subtraction is done for any data actions.

   ```Actions - NotActions = Effective management permissions ```

   ```DataActions - NotDataActions = Effective data permissions ```

7) If the user doesn't have a role with the action at the requested scope, access is not allowed. Otherwise, any conditions are evaluated.

8) If the role assignment includes conditions, they are evaluated. Otherwise access is allowed.

9) If conditions are met, access is allowed. Otherwise access is not allowed.

The following diagram is a summary of the evaluation logic.

![](https://github.com/amarnadh19/books/blob/main/images/az_rbac_7.png?)


## Assign Azure roles

### Using Azure portal

#### Step1: Identify the needed Scope

1) Sign to Azure portal

2) Search for Resource groups, Management groups, Subsciptions or other resource

3) Click the specific resource for that scope.

   The following shows an example resource group.

   ![](https://github.com/amarnadh19/books/blob/main/images/az_rbac_8.png?)


#### Step2: Open the Add role assignment pane

**Access control (IAM)** is a page that you typically use to assign roles to grant access to Azure resources. It is also known as identity and access management (IAM) and appers in several locations in the Azure portal.

1) Click Access Control (IAM)

   ![](https://github.com/amarnadh19/books/blob/main/images/az_rbac_9.png?)

2) Click the Role assignments tab to view the role assignments at this scope.

3) Click Add > Add role assignment. If you don't have permissions to assign roles, the Add role assignment option will be disabled.

   ![](https://github.com/amarnadh19/books/blob/main/images/az_rbac_10.png?)

  The Add role assignment pane opens.

  ![](https://github.com/amarnadh19/books/blob/main/images/az_rbac_11.png?)


#### Step3: Select the appropriate role

1) In the Role list, search or scroll to find the role that you want to assign.

   ![](https://github.com/amarnadh19/books/blob/main/images/az_rbac_12.png?)


#### Step4: Select Who needs access

1) In the Assign access to list, select the type of security principal to assign access to.

Type	                             Description
------------                        --------------
User, group, or service principal	 If you want to assign the role to a user, group, or  
                                     service principal (application), select this type.

User assigned managed identity	     If you want to assign the role to a user-assigned managed 
                                     identity, select this type.

System assigned managed identity	 If you want to assign the role to a system-assigned 
                                     managed identity, select the Azure service instance where the managed identity is located.
  ![](https://github.com/amarnadh19/books/blob/main/images/az_rbac_13.png?)

2) If you selected a user-assigned managed identity or a system-assigned managed identity, select the Subscription where the managed identity is located.

3) In the Select section, search for the security principal by entering a string or scrolling through the list.

  ![](https://github.com/amarnadh19/books/blob/main/images/az_rbac_14.png?)


#### Step5: Assign role

1) To assign the role, click Save.

2) On the Role assignments tab, verify that you see the role assignment in the list.

   ![](https://github.com/amarnadh19/books/blob/main/images/az_rbac_15.png?)


### Assign Azure roles using Azure PowerShell

#### Step1: Determine who need access

1) User

   To get the object ID, you can use ```Get-AzADUser```.

   ``` 
   Get-AzADUser -StartsWith <userName>
   (Get-AzADUser -DisplayName <userName>).id
   ```

2) Group

   To get the object ID, you can use ```Get-AzADGroup```.

   ```
   Get-AzADGroup -SearchString <groupName>
   (Get-AzADGroup -DisplayName <groupName>).id
   ```

3) Service Principal

   To get the object ID, you can use ```Get-AzADServicePrincipal```.

   ```
   Get-AzADServicePrincipal -SearchString <principalName>
   (Get-AzADServicePrincipal -DisplayName <principalName>).id
   ```

4) Managed identity

   To get the object ID, you can use ```Get-AzADServicePrincipal```.

   ```
   Get-AzADServicePrincipal -SearchString <principalName>
   (Get-AzADServicePrincipal -DisplayName <principalName>).id
   ```

#### Step2: Select the appropriate role

1) To list roles and get the unique role ID, you can use ```Get-AzRoleDefinition```.

   ```
   Get-AzRoleDefinition | FT Name, IsCustom, Id
   ```

#### Step3: Identify the needed scope.

1) Resource group scope

   you can use ```Get-AzResourceGroup```

   ```
   Get-AzResourceGroup
   ```

2) Subscription scope

   you can use ```Get-AzSubscription```

   ```
   Get-AzSubscription
   ```

3) Management group scope

   you can use ```Get-AzManagementGroup```

   ```
   Get-AzManagementGroup
   ```

#### Step4: Assign role

1) Resource scope

   ```
   New-AzRoleAssignment -ObjectId <objectId> -RoleDefinitionName <roleName> -Scope /subscriptions/<subscriptionId>/resourcegroups/<resourceGroupName>/providers/<providerName>/<resourceType>/<resourceSubType>/<resourceName>
   
   New-AzRoleAssignment -ObjectId <objectId> -RoleDefinitionId <roleId> -ResourceName <resourceName> -ResourceType <resourceType> -ResourceGroupName <resourceGroupName>
   
   ```

