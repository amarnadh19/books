# ARM templates

It shows you how to create a starter template and deploy it to Azure.


In Azure and Azure Stack, the Azure Resource Manager is the management layer (API) where you connect to for deploying resources. In this blog we are going to look at the Azure Resource Template and how to use it when deploying resources. When deploying resources with Azure Resource Manager keep in mind the following aspects. It is:

- **Template-driven** – Using templates to deploy all resources.

- **Declarative** – You declare the resources you want to have instead of imperative where you need to make rules.

- **Idempotent** – You can deploy the template over and over again without affecting the current state of resources.

- **Multi-service** – All services can be deployed using Azure Resource Manager, Website, Storage, VMs etc.

- **Multi region**- You can choose in which region you would like to deploy the resources.

- **Extensible** – Azure Resource Manager is extensible with more resource providers and thus resources.


## Template file


Within your template, you can write template expressions that extend the capabilities of JSON. These expressions make use of the functions provided by Resource Manager.

The template has the following sections:

- **Parameters** - Provide values during deployment that allow the same template to be used with different environments.

- **Variables** - Define values that are reused in your templates. They can be constructed from parameter values.

- **User-defined functions** - Create customized functions that simplify your template.

- **Resources** - Specify the resources to deploy.

- **Outputs** - Return values from the deployed resources.



## Tutorial: Create and deploy your first ARM template

### Creating Template

Create azuredeploy.json file. Note: `Use any file name with extension as .json`.

```

{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "resources": []
}
```

This template doesn't deploy any resources. We're starting with a blank template so you can get familiar with the steps to deploy a template while minimizing the chance of something going wrong.


The JSON file has these elements:

- **$schema:** Specifies the location of the JSON schema file. The schema file describes the properties that are available within a template. For example, the schema defines **resources** as one of the valid properties for a template. Don't worry that the date for the schema is 2019-04-01. This schema version is up to date and includes all of the latest features. The schema date hasn't been changed because there have been no breaking changes since its introduction.

- **contentVersion:** Specifies the version of the template (such as 1.0.0.0). You can provide any value for this element. Use this value to document significant changes in your template. When deploying resources using the template, this value can be used to make sure that the right template is being used.

- **resources:** Contains the resources you want to deploy or update. Currently, it's empty, but you'll add resources later.


### Creating Resource group using Azure CLI

```

az login

az group create \
  --name myResourceGroup \
  --location "Central US"

```

### Deploying template

```
az deployment group create \
  --name blanktemplate \
  --resource-group myResourceGroup \
  --template-file {provide the template file name}

```

The deployment command returns results. Look for *ProvisioningState* to see whether the deployment succeeded.

![](https://github.com/amarnadh19/books/blob/main/images/az_arm_1.png?)



## Tutorial: Add a resource to your ARM template

### Adding resource to Template file

```
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "resources": [
    {
      "type": "Microsoft.Storage/storageAccounts",
      "apiVersion": "2019-04-01",
      "name": "{provide-unique-name}",
      "location": "eastus",
      "sku": {
        "name": "Standard_LRS"
      },
      "kind": "StorageV2",
      "properties": {
        "supportsHttpsTrafficOnly": true
      }
    }
  ]
}

```

### Resource Properties

You may be wondering how to find the properties to use for each resource type. You can use the ARM template reference to find the resource types you want to deploy.

Every resource you deploy has at least the following three properties:

- **type:** Type of the resource. This value is a combination of the namespace of the resource provider and the resource type such as Microsoft.Storage/storageAccounts.

- **apiVersion:** Version of the REST API to use for creating the resource. Each resource provider publishes its own API versions, so this value is specific to the type.

- **name:** Name of the resource.


Most resources also have a **location** property, which sets the region where the resource is deployed.

The Microsoft.Storage resource provider could release a new API version, but the version you're deploying doesn't have to change.

You can see that API version at storageAccounts 2019-04-01.


### Deploy template

```
az deployment group create \
  --name addstorage \
  --resource-group myResourceGroup \
  --template-file {template file name}

```


## Tutorial: Add parameters to your ARM template

### Make template reusable

To make your template reusable, let's add a parameter that you can use to pass in a storage account name. The highlighted JSON in the following example shows what changed in your template. The storageName parameter is identified as a string. The maximum length is set to 24 characters to prevent any names that are too long.


```
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "parameters": {
    "storageName": {
      "type": "string",
      "minLength": 3,
      "maxLength": 24
    }
  },
  "resources": [
    {
      "type": "Microsoft.Storage/storageAccounts",
      "apiVersion": "2019-04-01",
      "name": "[parameters('storageName')]",
      "location": "eastus",
      "sku": {
        "name": "Standard_LRS"
      },
      "kind": "StorageV2",
      "properties": {
        "supportsHttpsTrafficOnly": true
      }
    }
  ]
}
```

### Deploy template

```
az deployment group create \
  --name addnameparameter \
  --resource-group myResourceGroup \
  --template-file {template file name} \
  --parameters storageName={your-unique-name}

```



