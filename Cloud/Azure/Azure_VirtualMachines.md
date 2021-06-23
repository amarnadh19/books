# Azure CLI

The Azure CLI is Microsoft's cross platform command line tool for managing azure resources. It's available for macOS,Linux and windows, or in the browser using **Azure Cloud Shell**  

To create, change or delete multiple things we can pass commands or use scripts to run the repetitive tasks
With Azure, you have 2 different command line tools: Azure Powershell and Azure CLI

## With either of these tools

- You can write scripts to check the status of cloud servers
- Deploy new configurations
- Open ports in the firewall or connect to virtusl machine to change the settings 

Windows admins tend to prefer Azure Powershell, While developers and Linux admins use the Azure CLI

## Creating VirtualMachine using Azure CLI

```
az vm create \
>   --resource-group <resource group name> \
>   --location westus \
>   --name SampleVM \
>   --image UbuntuLTS \
>   --admin-username azureuser \
>   --generate-ssh-keys  \
    --verbose
```    

### To connect Linux machine

ssh azureuser@<publicIP>

### To list the Images 

*az vm image list --output table*

### To list the Images with location

*az vm image list --location eastus --output table*

### To list the Images with Specific image name

*az vm image list --sku wordpress --output table --all*

## Predefined VM sizes:

When you create a virtual machine, you can supply a VM size value that will determine the amount of compute resources that will be devoted to the VM. This includes CPU, GPU, and memory that are made available to the virtual machine from Azure.

Azure defines a set of pre-defined VM sizes for Linux and Windows to choose from based on the expected usage.

## PRE-DEFINED VM SIZES
Type	                         Sizes	                                     Description
General purpose	 Dsv3, Dv3, DSv2, Dv2, DS, D, Av2, A0-7	   Balanced CPU-to-memory. Ideal for dev/test and small to medium applications 
                                                           and data solutions.
Compute optimized	Fs, F	                               High CPU-to-memory. Good for medium-traffic applications,
                                                           network appliances,  and batch processes.
Memory optimized	Esv3, Ev3, M, GS, G, DSv2, DS, Dv2, D  High memory-to-core. Great for relational databases, medium to
                                                           large  caches, and in-memory analytics.
Storage optimized	Ls	                                   High disk throughput and IO. Ideal for big data, SQL, and NoSQL databases.
GPU optimized	    NV, NC	                               Specialized VMs targeted for heavy graphic rendering and video editing.
High performance	H, A8-11	                          Our most powerful CPU VMs with optional high-throughput network interfaces (RDMA).

### Predefined VM sizes location wise
az vm list-sizes --location eastus --output table

### Create a vm 
```
az vm create \
    --resource-group <resource group-name> \
    --name SampleVM2 \
    --image UbuntuLTS \
    --admin-username azureuser \
    --generate-ssh-keys \
    --verbose \
    --size "Standard_DS2_v2"
```

We can also resize an existing VM if the workload changes, or if it was incorrectly sized at creation. Before a resize is requested, we must check to see if the desired size is available in the cluster our VM is part of. We can do this with the vm list-vm-resize-options command:

```
az vm list-vm-resize-options \
    --resource-group <resource group-name> \
    --name SampleVM \
    --output table
```

This will return a list of all the possible size configurations available in the resource group. If the size we want isn't available in our cluster, but is available in the region, we can deallocate the VM. This command will stop the running VM and remove it from the current cluster without losing any resources. Then we can resize it, which will re-create the VM in a new cluster where the size configuration is available.

### VM resizing

```
az vm resize \
    --resource-group <resource group-name> \
    --name SampleVM \
    --size Standard_D2s_v3
```

### To list the IP address
az vm list-ip-addresses -n SampleVM -o table


## Adding filters to quires with JMESPath
JMESPath is an industry-standard query language built around JSON objects. The simplest query is to specify an identifier that selects a key in the JSON object.

### To list different parameters of VM
```
az vm show \
    --resource-group <resource group-name> \
    --name SampleVM \
    --query "osProfile.adminUsername"

az vm show \
    --resource-group <resource group-name> \
    --name SampleVM \
    --query hardwareProfile.vmSize
```

#### To retrieve all the IDs for your network interfaces, you can run the query:

```
az vm show \
    --resource-group <resource group-name> \
    --name SampleVM \
    --query "networkProfile.networkInterfaces[].id"
```

If you decide to use it this way, a useful flag to add is the --output tsv parameter (which can be shortened to -o tsv). This will return the results in tab-separated values that only include the actual data values with tab separators.

```
az vm show \
    --resource-group <resource group-name> \
    --name SampleVM \
    --query "networkProfile.networkInterfaces[].id" -o tsv
```
### To stop the VM
```
az vm stop \
    --name SampleVM \
    --resource-group <resource group-name>
```
### To check the VM status
```
az vm get-instance-view \
    --name SampleVM \
    --resource-group <resource group-name> \
    --query "instanceView.statuses[?starts_with(code, 'PowerState/')].displayStatus" -o tsv
output: VM stopped

az vm start \
    --name SampleVM \
    --resource-group <resource group-name>
az vm restart \
    --name SampleVM \
    --resource-group <resource group-name>
    -- no-wait
```

### To open the port

```
az vm open-port \
    --port 80 \
    --resource-group <resource group-name> \
    --name SampleVM
```

