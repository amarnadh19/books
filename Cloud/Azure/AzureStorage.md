# Azure Storage

Azure Storage is Microsoft's cloud storage solution for modern data storage scenarios.

Azure Storage is:

- **Durable and Highly available.** Redundancy ensures that your data is safe in the event of transient hardware failures. You can also opt to replicate data across datacenters or geographical regions for additional protection
Below are storage types available in Azure.

- **Secure.** All data written to an Azure storage account is encrypted by the service. Azure Storage provides you with fine-grained control over who has access to your data.

- **Scalable.** Azure Storage is designed to be massively scalable to meet the data storage and performance needs of today's applications.

- **Managed.** Azure handles hardware maintenance, updates, and critical issues for you.

- **Accessible.** Data in Azure Storage is accessible from anywhere in the world over HTTP or HTTPS


Azure storage in three categories.

- **Storage for Virtual Machines.** This includes disks and files. Disks are persistent block storage for Azure IaaS Virtual machines. Files are fully managed file shares in the cloud.

- **Unstructured Data.** This includes Blobs and Data Lake Store. Blobs are highly scaleable, REST based cloud object store. Data Lake store is Hadoop Distributed File System (HDFS) as a service.

- **Structured Data.** This includes Tables. Tables are key/value, auto-scaling NoSQL store.

General Purpose Storage accounts have two tiers: **Standard** and **Premium**.

- **Standard** Backup by HDD and provide the lowest cost per GB. Good for apps which requires bulk storage or where data is accessed infrequetly (old storage)

- **Premium** are backed up SSD, Offers consistent low latency performance. Good for fast accessing data like Database.

*We cannot convert from standard to premium or viceversa. Have to create a new one and copy data.*


## Core Storage services

Different types of Storage options available in Azure:

    - Blob storage
    - Azure files
    - Azure queues
    - Azure tables
    - Azure disks

To use Azure storage, we need **Storage account**.

Azure VMs use Azure Disk storage to store virtual disks. Azure Disk storage cannot be used to store data outside the VM.

## Azure Storage account

An Azure storage account contains all of your Azure Storage data objects: blobs, file shares, queues, tables, and disks.

The storage account provides a unique namespace for your Azure Storage data that's accessible from anywhere in the world over HTTP or HTTPS.

Data in your storage account is durable and highly available, secure, and massively scalable.

### Types of Storage Account

Azure Storage offers serveral types of storge accounts. The types of storage accounts are:

![](https://github.com/amarnadh19/books/blob/main/images/az_storage6.PNG?)

- **General-purpose v1 accounts (Storage):**
  - Legacy account type of blobs, files, queues, and tables.
  - Use general-purpose V2 accounts instead when possible.

- **General-purpose V2 accounts (StorageV2):**
  - Basic storage account type for blobs, files, queues, and tables.
  - Recommended for most scenarios using Azure Storage.
  - For NFS use premium file share account type.

- **Block blob storage accounts (BlockBlobStorage):**
  - Blob-only storage accounts with premium performance.
  - Premium storage type for Block blob and append blob.
  - Recommended for scenarios with high transactions rates, using smaller objects, or requiring consistently low storage latency.

- **FileStorage storage accounts (FileStorage):**
  - Files-only storage accounts with premium performance characteristics.
  - Recommended for enterprise or high performance scale appllications.
  - Supports both SMB and NFS protocols.

- **Premium page blobs:**
  - For page blobs only
  - Premium storage account type for page blobs.
  - SSD drives for low latency and high throughput.
  - Supports only LRS

### Storage account Endpoints

- Every object that you store in Azure Storage has an address that includes your unique account name.

- The combination of the account name and the Azure Storage service endpoint forms the endpoints for your storage account.

#### When naming your storage account, keep these rules in mind:

- Storage account names must be between 3 and 24 characters in length and may contain numbers and lowercase letters only.
- Your storage account name must be unique within Azure. No two storage accounts can have the same name.

![](https://github.com/amarnadh19/books/blob/main/images/az_storage7.PNG?)

Construct the URL for accessing an object in a storage account by appending the object's location in the storage account to the endpoint. For example, the URL for a blob will be similar to:

```http://*mystorageaccount*.blob.core.windows.net/*mycontainer*/*myblob*```


### Creation of Storage account

#### Creation of Storage account using Azure portal

Below Screenshots show how to create Storage account.

![](https://github.com/amarnadh19/books/blob/main/images/az_storage18.png?)

![](https://github.com/amarnadh19/books/blob/main/images/az_storage19.png?)


#### Create Storage account using Azure CLI

Use the ```az storage account``` create command to create the storage account. You can enter the command into the Cloud Shell window on the right.

``` 

amarnadh_t@Azure:~$ az storage account create --name queuestorag234567e -g learn-08afede4-6043-4d0b-9add-9b3a449cd9ac --kind StorageV2 --sku Standard_LRS
{
  "accessTier": "Hot",
  "allowBlobPublicAccess": null,
  "allowCrossTenantReplication": null,
  "allowSharedKeyAccess": null,
  "azureFilesIdentityBasedAuthentication": null,
  "blobRestoreStatus": null,
  "creationTime": "2021-06-03T05:01:54.329182+00:00",
  "customDomain": null,
  "enableHttpsTrafficOnly": true,
  "enableNfsV3": null,
  "encryption": {
    "encryptionIdentity": null,
    "keySource": "Microsoft.Storage",
    "keyVaultProperties": null,
    "requireInfrastructureEncryption": null,
    "services": {
      "blob": {
        "enabled": true,
        "keyType": "Account",
        "lastEnabledTime": "2021-06-03T05:01:54.438557+00:00"
      },
      "file": {
        "enabled": true,
        "keyType": "Account",
        "lastEnabledTime": "2021-06-03T05:01:54.438557+00:00"
      },
      "queue": null,
      "table": null
    }
  },
  "extendedLocation": null,
  "failoverInProgress": null,
  "geoReplicationStats": null,
  "id": "/subscriptions/1aaf9514-a838-4b16-9737-bd8e019e73de/resourceGroups/learn-08afede4-6043-4d0b-9add-9b3a449cd9ac/providers/Microsoft.Storage/storageAccounts/queuestorag234567e",
  "identity": null,
  "isHnsEnabled": null,
  "keyCreationTime": {
    "key1": "2021-06-03T05:01:54.422942+00:00",
    "key2": "2021-06-03T05:01:54.422942+00:00"
  },
  "keyPolicy": null,
  "kind": "StorageV2",
  "largeFileSharesState": null,
  "lastGeoFailoverTime": null,
  "location": "westus",
  "minimumTlsVersion": null,
  "name": "queuestorag234567e",
  "networkRuleSet": {
    "bypass": "AzureServices",
    "defaultAction": "Allow",
    "ipRules": [],
    "resourceAccessRules": null,
    "virtualNetworkRules": []
  },
  "primaryEndpoints": {
    "blob": "https://queuestorag234567e.blob.core.windows.net/",
    "dfs": "https://queuestorag234567e.dfs.core.windows.net/",
    "file": "https://queuestorag234567e.file.core.windows.net/",
    "internetEndpoints": null,
    "microsoftEndpoints": null,
    "queue": "https://queuestorag234567e.queue.core.windows.net/",
    "table": "https://queuestorag234567e.table.core.windows.net/",
    "web": "https://queuestorag234567e.z22.web.core.windows.net/"
  },
  "primaryLocation": "westus",
  "privateEndpointConnections": [],
  "provisioningState": "Succeeded",
  "resourceGroup": "learn-08afede4-6043-4d0b-9add-9b3a449cd9ac",
  "routingPreference": null,
  "sasPolicy": null,
  "secondaryEndpoints": null,
  "secondaryLocation": null,
  "sku": {
    "name": "Standard_LRS",
    "tier": "Standard"
  },
  "statusOfPrimary": "available",
  "statusOfSecondary": null,
  "tags": {},
  "type": "Microsoft.Storage/storageAccounts"
}

```



## Azure Storage account replication

### Redundancy in the Primary Region

Data in an Azure Storage account is always replicated three times in the primary region.

Azure Storage offers two options for how your data is replicated in the primary region:

- Locally Redundant Storage (LRS)
- Zone-redundant Storage (ZRS)

    Microsoft recommends using ZRS in the primary region for Azure Data Lake Storage Gen2 Workloads.

#### Locally Redundant Storage (LRS)

- replicate your data three times within a single data center in primary region.
- Offers 99.999999999(11 nines) durability over an year
- Lowest cost redundancy option and offers the least durablility.
- Protects again server rack failures.
- A write request happens synchronously. The write operation returns successfully only after the data is written to all three replicas.
- The following diagram shows how your data is replicated within a single data center with LRS:

![](https://github.com/amarnadh19/books/blob/main/images/az_storage8.PNG?)

LRS is a good choice for the following scenarios:

  - If your application stores data that can be easily reconstructed if data loss occurs, you may opt for LRS.
  - If your application is restricted to replicating data only within a country or region due to data governance requirements


#### Zone-redundant storage (ZRS)

- Zone-redundant storage (ZRS) replicates your Azure Storage data synchronously across three Azure availability zones in the primary region.
- Durabililty 99.999999999999% (12 nines) over a year.
- With ZRS, your data is still accessible for both read and write operations even if a zone becomes unavailable.
- When designing applications for ZRS, follow practices for transient fault handling, including implementing retry policies with exponential back-off.
- A write request to a storage account that is using ZRS happens synchronously.
- The write operation returns successfully only after the data is written to all replicas across the three availability zones.
- Microsoft recommends using ZRS in the primary region for scenarios that require high availability.

The following diagram shows how your data is replicated across availability zones in the primary region with ZRS:

![](https://github.com/amarnadh19/books/blob/main/images/az_storage9.PNG?)

### Redundancy in a secondary region

When you create a storage account, you select the primary region for the account. The paired secondary region is determined based on the primary region, and can't be changed.

- Geo-redundant storage (GRS)
- Geo-zone-redundant storage (GZRS)

With GRS or GZRS, the data in the secondary region isn't available for read or write access unless there is a failover to the secondary region.

For read access to the secondary region, configure your storage account to use read-access geo-redundant storage (RA-GRS) or read-access geo-zone-redundant storage (RA-GZRS).

#### Geo-redundant storage

- Geo-redundant storage (GRS) copies your data synchronously three times within a single physical location in the primary region using LRS.
- durability 99.99999999999999% (16 9's) over a given year.
- A write operation is first committed to the primary location and replicated using LRS.
- The update is then replicated asynchronously to the secondary region. When data is written to the secondary location, it's also replicated within that location using LRS.

The following diagram shows how your data is replicated with GRS or RA-GRS:
![](https://github.com/amarnadh19/books/blob/main/images/az_storage10.PNG?)


#### Geo-zone-redundant storage

- Geo-zone-redundant storage (GZRS) combines the high availability provided by redundancy across availability zones with protection from regional outages provided by geo-replication
- Data in a GZRS storage account is copied across three Azure availability zones in the primary region and is also replicated to a secondary geographic region for protection from regional disasters.
- Microsoft recommends using GZRS for applications requiring maximum consistency, durability, and availability, excellent performance, and resilience for disaster recovery.
- durability 99.99999999999999% (16 9's) over a given year.

The following diagram shows how your data is replicated with GZRS or RA-GZRS:

![](https://github.com/amarnadh19/books/blob/main/images/az_storage11.PNG?)

Only general-purpose v2 storage accounts support GZRS and RA-GZRS.

### Read access to data in the secondary region

- For read access to the secondary region, enable read-access geo-redundant storage (RA-GRS) or read-access geo-zone-redundant storage (RA-GZRS).

    Note:

    Azure Files does not support read-access geo-redundant storage (RA-GRS) and read-access geo-zone-redundant storage (RA-GZRS).

#### RA-GRS

- durability 99.99999999999999% (16 9's) over a given year.
- When using RA-GRS you need to ensure that your applications known which end point it is interating with.
- RA-GRS is ideal for application which requires HA.
- Provides only Read only access is secondary region.

![](https://github.com/amarnadh19/books/blob/main/images/az_storage15.PNG?)

    Note:

    The Main difference between GRS and GZRS is:

    GRS data is replicated 3 times in primary region using LRS and one copy is ansync with secondary region i.e secondary region has only one copy.

The following table describes key parameters for each redundancy option:

![](https://github.com/amarnadh19/books/blob/main/images/az_storage12.PNG?)

Supported storage account types

![](https://github.com/amarnadh19/books/blob/main/images/az_storage13.PNG?)

Supported Azure Storage services

![](https://github.com/amarnadh19/books/blob/main/images/az_storage14.PNG?)



## Storage Pricing

All storage accounts use a pricing model for blob storage based on the tier of each blob. When using a storage account, the following billing considerations apply:

- **Performance tiers:** In addition to, amount of daa stored, the cost of storing data varies deponding on the storage tier. The per-GB gost decreases as the tier gets cooler.

- **Data access costs:** Data access charges increase as the tier gets cooler. For data in the cool and archive storage tier, you are charged a per-gigabyte data access charge for reads.

- **Transaction Costs:** There is a per-transaction charge for all tiers that increases as the tier gets cooler.

- **Geo-Replication data Transfer costs:** This charge only applies to accounts with Geo-replication configured, including GRS and RA-GRS. It occurs per GB

- **Outbound data transfer costs:** Outbound data transfers (data transfered out of an Azure region) incur billing for bandwidth usage on a per GB basis, Consistent with General-purpose storage accounts.

- **Changing the storage tier:** Changing the account storage tier from cool to hot incurs a charge equal to reading all the data existing in the storage account. However, changing the account storage from Hot to Cool incurs a charge equal to writing all the data into the cool tier (GPv2 accounts only).


## Azure Blob storage

Blob storage can store any type of test or binary data, such as document, media file, or application installer.

Blob storage can be referred as object storage.

**Common uses of Blob storage include:**

- Serving images or documents idrectly to a browser.

- Storing files for distributed access, such as installation.

- Streaming video and audio.

- Storing dsata for backup and restore, disaster recovery, and archiving.

- Storing data for analysis by an on-premises or Azure-Hosted service.


### Blob Service resources

Blob storage offers three types of resources:

- The storage account

- Containers in the storage account

- Blobs in a container

The following diagram shows the relationship between these resources.

![](https://github.com/amarnadh19/books/blob/main/images/az_storage1.PNG?)

    Within the storage account, you can group as many blobs as needed in a container.

### Storage accounts

A storage account provides a unique namespace in Azure for your data. Every object that you store in Azure Storage has an address that includes your unique account name. The combination of the account name and the Azure Storage blob endpoint forms the base address for the objects in your storage account.

For example, if your storage account is named mystorageaccount, then the default endpoint for Blob storage is:

**http://mystorageaccount.blob.core.windows.net**


### Containers

A container organizes a set of blobs, similar to a directory in a file system. A storage account can include an unlimited number of containers, and a container can store an unlimited number of blobs.

All Blobs must be in a container.

An account can have unlimited containers.

You can create container in azure portal. refer below image

![](https://github.com/amarnadh19/books/blob/main/images/az_storage2.PNG?)

    ** Name ** : The name is 3-63 chars long. Name contains lower case letters, Hyphens. Name should start with letter or a number.
    ** Public access level **
        - Use **Private** to ensure no anonymous access.
        - Use **Blob** to allow anonymous public read access for blobs only.
        - Use **Container** to allow anonymous public read and list access to the eintire container, including blobs


### Blobs

There are three types of blobs in Azure

- **Block Blob** store text and binary data. Block blobs are made up of blocks of data that can be managed individually. Block blobs can store up to about 190.7 TiB.

- **Append Blob** are made up of blocks like block blobs, but are optimized for append operations. Append blobs are ideal for scenarios such as logging data from virtual machines.

- **Page Blob** store random access files up to 8 TiB in size. Page blobs store virtual hard drive (VHD) files and serve as disks for Azure virtual machines.


*You can also create the Blob container with PowerShell using the* ```New-AzStorageContainer```

### Blob Access Tiers

Azure Storage provides different options for accessing block blob data based on usage.

By selecting the correct access tier for your needs, you can store your block blob data in the most cost-effective manner.

![](https://github.com/amarnadh19/books/blob/main/images/az_storage3.PNG?)

- **Hot** For frequent access of objects in the storage account. Accessing data in the Hot tier is most cost-effective, while storage costs are somewhat higher.

- **Cool** For infrequently accessed data. Large amount of data can be stored. Data can be stored atleast 30days. More cost effective, but accessing data may be somewhat more expensive than Hot tier.

- **Archive** Can tolerate for several hours of retrieval latency and will remain in the Archive tier for at least 180 days. Most cost effective but data reterval is costly than Hot or Cold tier.

*You can shift between tiers any time*

### Blob life cycle management

![](https://github.com/amarnadh19/books/blob/main/images/az_storage4.PNG?)

Azure Blob storage lifecycle management offers a rich, rule-based policy for GPv2 and Blob storage accounts.

The lifecycle management policy lets you:

- Transition blobs to a cooler storage tier to optimize performance and cost.

- Delete blobs at the end of their lifecycles.

- Define rules to be run once per day at the storage account level.

- Apply rules to containers or a subset of blobs (using prefixes as filters).


### Uploading Blobs

A blob can be any type and size file. Azure Storage offers three types *block blob, Append blob and page blob*. You have to mention the type of blob where data to be stored.

Below screenshot has more information.

![](https://github.com/amarnadh19/books/blob/main/images/az_storage5.PNG?)

Once the blob has been created, it cannot be changed.

#### Blob Upload tools

There are multiple methods to upload data to blob storage

- **AzCopy** is an easy-to-use command-line tool for Windows and Linux that copies data to and from Blob storage, across containers, or across storage accounts.

- The **Azure Storage Data Movement** library is a .NET library for moving data between Azure Storage services. The AzCopy utility is built with the Data Movement library.

- **Azure Data Factory** supports copying data to and from Blob storage by using the account key, a shared access signature, a service principal, or managed identities for Azure resources.

- **Blobfuse** is a virtual file system driver for Azure Blob storage. You can use blobfuse to access your existing block blob data in your Storage account through the Linux file system.

- **Azure Data Box** service is available to transfer on-premises data to Blob storage when large datasets or network constraints make uploading data over the wire unrealistic. Depending on your data size, you can request Azure D*ata Box Disk, Azure Data Box, or Azure Data Box Heavy devices* from Microsoft. You can then copy your data to those devices and ship them back to Microsoft to be uploaded into Blob storage.

- The **Azure Import/Export** service provides a way to import or export large amounts of data to and from your storage account using hard drives that you provide.

- **Azure Storage Explorer** also can be used


## AzureFiles

### What are Azure files?

Azure Files enables you to set up highly available network file shares that can be accessed by using the standard Server Message Block (SMB) protocol. That means that multiple VMs can share the same files with both read and write access. You can also read the files using the REST interface or the storage client libraries.

![](https://github.com/amarnadh19/books/blob/main/images/az_storage16.PNG?)

Azure file shares can be mounted concurrently by cloud or on-premises deployments.

Azure Files SMB file shares are accessible from Windows, Linux, and macOS clients.

Azure Files NFS file shares are accessible from Linux or macOS clients.

Azure Files SMB file shares can be cached on Windows Servers with Azure File Sync for fast access

*One difference between Azure files and files on corporate fileshare is you can access the files from anywhere in the world using URL and inludes a shared Access Signature(SAS) token*

you can generate the SAS tokens, they allow specific access to private asset for specifc amount of time

### Choose your data access method

There are two built-in methods of data access supported by Azure Files.

- One method is direct access via a mounted drive in your operating system.

- The other method is to use a Windows server (either on-premises or in Azure) and install Azure File Sync to synchronize the files between local shares and Azure Files.

### Choose your file redundancy option

Because Azure Files stores files in a storage account, you can choose between standard or premium performance storage accounts:

- **Standard performance:** Double-digit ms latency, 10,000 IOPS, 300-MBps bandwidth.

- **Premium performance:** Single-digit ms latency, 100,000 IOPS, 5-GBps bandwidth.

  Note:

  Premium File storeage accounts with ZRS are only supported in a smaller subset of regions.

### FileShare Common scenarios:

- Many on-premises applications use file shares. This feature makes it easier to migrate those applications that share data to Azure. If you mount the file share to the same drive letter that the on-premises application uses, the part of your application that accesses the file share should work with minimal, if any, changes.

- Configuration files can be stored on a file share and accessed from multiple VMs. Tools and utilities used by multiple developers in a group can be stored on a file share, ensuring that everybody can find them, and that they use the same version.

- Resource logs, metrics, and crash dumps are just three examples of data that can be written to a file share and processed or analyzed later.


## Queue storage

### What is Azure Queue Storage?

Azure Queue storage is an Azure service that implements cloud-based queues

The Azure Queue service is used to store and retrieve messages.

Accessing messages from anywhere in the world via authenticated calls using HTTP or HTTPS.

Application components access a queue using a REST API or an Azure-supplied client library.

Queue messgaes can be upto 64 KB in size, and a queue can contain million of messages,upto the total capacity limit of storage account.

Queues are generally used to store lists of messgaes to be processed asynchronously

Typically, you will have one or more **sender components** and one or more **receiver components**.

**Sender components** add messages to the queue. **Receiver components** retrieve messages from the front of the queue for processing.

A queue must be part of a storage account

The following illustration shows multiple sender applications adding messages to the Azure Queue and one receiver application retrieving the messages.

![](https://github.com/amarnadh19/books/blob/main/images/az_storage17.png?)

Pricing is based on queue size and number of operations. Larger message queues cost more than smaller queues. 

Charges are also incurred for each operation, such as adding a message and deleting a message. 

### Why use queues?

A queue increases resiliency by temporarily storing waiting messages. At times of low or normal demand, the size of the queue remains small because the destination component removes messages from the queue faster than they are added.

At times of high demand, the queue may increase in size, but messages are not lost. The destination component can catch up and empty the queue as demand returns to normal.

A single queue can be up to 500 TB in size, so it can potentially store millions of messages. The target throughput for a single queue is 2000 messages per second, allowing it to handle high-volume scenarios.

Azure Queue storage instantaneously handles high demand by storing messages until processing resources are available.

### What is a message?

A message in a queue is a byte array of up to 64 KB. Message contents are not interpreted at all by any Azure component.

If you want to create a structured message, you could format the message content using XML or JSON. Your code is responsible for generating and interpreting your custom format. For example, you could make a custom JSON message that looks like the following:

```
{
    "Message": {
        "To": "news@contoso.com",
        "From": "writer@contoso.com",
        "Subject": "Support request",
        "Body": "Send me a photographer!"
    }
}
```

### Queue storage concepts   

- URL format: Queues are addressable using the following URL format:

  https://<storage account>.queue.core.windows.net/<queue>

  The following URL addresses a queue in the diagram:

   https://myaccount.queue.core.windows.net/images-to-download

- **Storage account:** All access to Azure Storage is done through a storage account.
- **Queue:** A queue contains a set of messages. The queue name must be all lowercase
- **Message:** A message, in any format, of up to 64 KB. Before version 2017-07-29, the maximum time-to-live allowed is seven days.
               For version 2017-07-29 or later, the maximum time-to-live can be any positive number, or -1 indicating that the message doesn't expire. If this parameter is omitted, the default time-to-live is seven days.

### Settings for queues


When you create a storage account that will contain queues, you should consider the following settings:

- Queues are only available as part of Azure general-purpose storage accounts (v1 or v2). You cannot add them to Blob storage accounts.

- The Access tier setting which is shown for StorageV2 accounts applies only to Blob storage and does not affect queues.

- You should choose a location that is close to either the source components or destination components or (preferably) both.

- Data is always replicated to multiple servers to guard against disk failures and other hardware problems. You have a choice of replication strategies: Locally Redundant Storage (LRS) is low-cost but vulnerable to disasters that affect an entire data center while Geo-Redundant Storage (GRS) replicates data to other Azure data centers. 

- The performance tier determines how your messages are stored: Standard uses magnetic drives while Premium uses solid-state drives. Choose Standard if you expect peaks in demand to be short. Consider Premium if queue length sometimes becomes long and you need to minimize the time to access messages.

- Require secure transfer if sensitive information may pass through the queue. This setting ensures that all connections to the queue are encrypted using Secure Sockets Layer (SSL).


### Identify a queue

To access a queue, you need three pieces of information:

- Storage account name
- Queue name
- Authorization token

#### Queue identity

Every queue has a name that you assign during creation. The name must be unique within your storage account but doesn't need to be globally unique (unlike the storage account name).

#### Access authorization

Every request to a queue must be authorized and there are several options to choose from.

![](https://github.com/amarnadh19/books/blob/main/images/az_storage20.png?)

#### Retrieving the account key

```
Azure CLI

az storage account keys list --account-name <your storage account name>

```
```
Powershell

Get-AzStorageAccountKey ...
```

### Accessing queues

You access a queue using a REST API. To do this, you'll use a URL that combines the name you gave the storage account with the domain queue.core.windows.net and the path to the queue you want to work with. For example: http://<storage account>.queue.core.windows.net/<queue name>. An Authorization header must be included with every request. The value can be any of the three authorization styles.



## Table Storage

**Azure Table storage is now part of Azure Cosmos DB**. Azure Table storage is a service that stores non-relational structured data (known as structured NoSQL data) in the cloud, providing a key/attribute store with schemaless design. Because Table Storage is schemaless, it's easy to adopt your data as the application evolve

Access to table storage is fast and cost effective for many types of applications, typically low cost than traditional SQL for same volume of data

The service is a NoSQL datastore which accepts authenticated calls from inside and outside the Azure cloud

you can use Table storage to store flexible datasets like user data for web application, address books, device information or other typr of metadata your service requires

you can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account

Azure tables are ideal for storing structured, non-relational data.

### Common uses of Table storage include

- Storing TBs of structured data capable of serving web scale applications

- Storing datasets that don't require complex joins, foreign keys, or stored procedures and can be denormalized for fast access

- Quickly querying data using a clustered index

- Accessing data using the OData protocol and LINQ queries with WCF Data Service .NET Libraries.

### Table storage concepts

Table storage contains the following components:

![](https://github.com/amarnadh19/books/blob/main/images/az_storage21.png?)

- **URL format:** Azure Table Storage accounts use this format: http://<storage account>.table.core.windows.net/<table>

  **Azure Cosmos DB Table** API accounts use this format: http://<storage account>.table.cosmosdb.azure.com/<table>

  You can address Azure tables directly using this address with the OData protocol. 

- **Accounts:** All access to Azure Storage is done through a storage account. 

  All access to Azure Cosmos DB is done through a Table API account. See Create a Table API account for details creating a Table API account.

- **Table:** A table is a collection of entities. Tables don't enforce a schema on entities, which means a single table can contain entities that have different sets of properties.

- **Entity:** An entity is a set of properties, similar to a database row. An entity in Azure Storage can be up to 1MB in size. An entity in Azure Cosmos DB can be up to 2MB in size.

- **Properties:** A property is a name-value pair. Each entity can include up to 252 properties to store data. Each entity also has three system properties that specify a partition key, a row key, and a timestamp. Entities with the same partition key can be queried more quickly, and inserted/updated in atomic operations. An entity's row key is its unique identifier within a partition.

