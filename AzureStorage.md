# Table of contents

1. [Azure Storage] (#AzureStorage)



# Azure Storage <a name="AzureStorage"></a>

Below are storage types available in Azure.

    - Blob storage
    - Azure files
    - Azure queues
    - Azure tables
    - Azure disks

To use Azure storage, we need **Storage account**.

Azure VMs use Azure Disk storage to store virtual disks. Azure Disk storage cannot be used to store data outside the VM.

## Azure Storage account

Types of Storage Account 

## Storage Pricing

All storage accounts use a pricing model for blob storage based on the tier of each blob. When using a storage account, the following billing considerations apply:

- **Performance tiers:** In addition to, amount of daa stored, the cost of storing data varies deponding on the storage tier. The per-GB gost decreases as the tier gets cooler.

- **Data access costs:** Data access charges increase as the tier gets cooler. For data in the cool and archive storage tier, you are charged a per-gigabyte data access charge for reads.

- **Transaction Costs:** There is a per-transaction charge for all tiers that increases as the tier gets cooler.

- **Geo-Replication data Transfer costs:** This charge only applies to accounts with Geo-replication configured, including GRS and RA-GRS. It occurs per GB

- **Outbound data transfer costs:** Outbound data transfers (data transfered out of an Azure region) incur billing for bandwidth usage on a per GB basis, Consistent with General-purpose storage accounts.

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

## azure Storage Replication

