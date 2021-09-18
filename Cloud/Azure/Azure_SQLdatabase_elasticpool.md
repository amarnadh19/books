# Azure SQL database Elasticpools

## Introduction

SQL database elastic pools are a cost-effective service that can manage and scale multiple Azure SQL databases that have varying and unpredictable resource requirements.

Software as a service (SaaS) providers, like the fitness company, often need to provision a SQL database for each customer; in our case, for each location. As a service provider, you'll need to react to unpredictable workloads, especially when storing customer data. You may not have visibility as to how quickly each client will grow, or when demand will spike

## What is a SQL elastic pool?

SQL elastic pools are a resource allocation service used to scale and manage the performance and cost of a group of Azure SQL databases.

Elastic pools allow you to purchase resources for the group.

You set the amount of resources available to the pool, add databases to the pool, and set minimum resource limits for the databases within the pool.

## When to use an elastic pool?

SQL elastic pools are ideal when you have several SQL databases that have a low average utilization, but have infrequent, high utilization spikes.

## Create an elastic pool

SQL elastic pools must be hosted in a SQL server. You'll specify an existing server, or create a new server when creating an elastic pool.

Like many Azure resources, elastic pools can be created from the Azure portal, or the Azure CLI running the az sql elastic-pools create command, or via PowerShell running the ```New-AzSqlElasticPool``` command.

## Add databases to an elastic pool

Databases can be added using the Azure portal, the Azure CLI, or PowerShell.

When using the portal, you can add a new pool to an existing SQL server. Or, you can create a new SQL elastic pool resource and specify the server.

When using the CLI, call az sql db create, and specify the pool name using the --elastic-pool-name parameter. This command can move an existing database into the pool, or create a new one if it doesn't exist.

When using PowerShell, you can assign new databases to a pool using New-AzSqlDatabase, and move existing databases using Set-AzSqlDatabase.

You can add existing Azure SQL databases from your Azure SQL server into the pool, or create new databases. And you can mix service tiers within the same pool.


ADMIN_LOGIN="ServerAdmin"
RESOURCE_GROUP=learn-1b051876-6491-40c1-a047-282a65a23464
SERVERNAME=FitnessSQLServer-$RANDOM
LOCATION=westus2
PASSWORD=password@123