# Azure Networking

Virtual Neworks (VNets) are used in Azure to provide private conneectivity between Azure Virtual machine and other Azure services.

VMs and services that are part of the same virtual network can access one another.

By default, services outside the virtual network cannot connect to services within the virtual network.

You can configure the network to allow access to the external service, including your on-premises servers.

Azure Virtual Network (VNet) is the fundamental building block for your private network in Azure.

VNet enables many types of Azure resources, such as Azure Virtual machines (VM) to securely communicate with each other, the internet, and on-premises networks.

## VNet concepts

- **Address Space**:
  - When creating a VNet, you must specify a custom private IP address space using Public and private addresses.
  
  - Azure assigns resources in a virtual network a private IP address from the address space that you assign.

- **Subnets**:
  - Subnets enable you to segment the virtual network into one or more sub networks and allocate a portion of the virtual network's address space to each subnet.
  
  - You can then deploy Azure resources in a specific subnet.

  - You can secure resources within subnets using Network Security Group.

- **Regions**:
  - VNet is scoped to a single region/location; However, multiple virtual networks from different regions can be connected together using *Virtual Network Peering*. 

  - You can also use a VPN gateway to send traffic between VNets.

