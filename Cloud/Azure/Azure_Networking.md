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

  ![](https://github.com/amarnadh19/books/blob/main/images/az_networking_1.png?)

- **subscription**:
  - VNet is scoped to a subscription. You can implement multiple VNets with in each Azure subscription and Azure region.

## Best Practices

- Ensure non-overlapping address spaces with on-prem network.

- Your subnet should not cover the entire address space of the VNet. Plan ahead and reserve some address space for the future.

- It is recommended you have fewer large VNets than Multiple Small VNets. This will prevent management overhead.

- Secure your VNet's by assigning Network Security Groups (NSGs) to the subnets beneath them.


## Communicate with the internet

By default, all resources in a VNet can communicate outbound to the internet.

You can communicate inbound to a resource by assigning a public IP address or a public Load Balancer. 

You can also use public IP or public Load Balancer to manage your outbound connections.

  Note:

  When using only an internal Standard LB, outbound connectivity is not available until you define how you want outbound connections to work with an instance level public IP or a Public LB.

## Communicate between Azure resources

Azure resources communicate securely with each other in one of the following ways:

- **Through a virtual network:** 
  - You can deploy VMs, and several other types of Azure resources to a virtual network, such as Azure App Service Environments, the Azure Kubernetes Service (AKS), and Azure Virtual Machine Scale Sets. 

- **Through a virtual network service endpoint:** 
  - Extend your virtual network private address space and the identity of your virtual network to Azure service resources, such as Azure Storage accounts and Azure SQL Database, over a direct connection. 
  
  - *Service endpoints* allow you to secure your critical Azure service resources to only a virtual network. 

- **Through VNet Peering:** 
  - You can connect virtual networks to each other, enabling resources in either virtual network to communicate with each other, using *virtual network peering*. 
  
  - The virtual networks you connect can be in the same, or different, Azure regions.

- **Through Private Link**:
  - You can access Azure PaaS services (For example, Azure Storage and SQL Database) and Azure hosted customer-owned/partner services over a private endpoint in a virtual network.

## Communicate with on-premises resources

You can connect your on-premises computers and networks to a virtual network using any combination of the following options:

- **Point-to-site virtual private network (VPN) (P2S VPN):** 
  - Established between a virtual network and a single computer in your network. 
  
  - Each computer that wants to establish connectivity with a virtual network must configure its connection. 
  
  - This connection type is great if you're just getting started with Azure, or for developers, because it requires little or no changes to your existing network. 
  
  - The communication between your computer and a virtual network is sent through an encrypted tunnel over the internet. 

- **Site-to-site VPN (S2S VPN):** 
  - Established between your on-premises VPN device and an Azure VPN Gateway that is deployed in a virtual network. 
  
  - This connection type enables any on-premises resource that you authorize to access a virtual network. 
  
  - The communication between your on-premises VPN device and an Azure VPN gateway is sent through an encrypted tunnel over the internet. 

- **Azure ExpressRoute:** 
  - Established between your network and Azure, through an ExpressRoute partner. This connection is private. Traffic does not go over the internet. To learn more, see ExpressRoute.

## Filter network Traffic

You can filter network traffic between subnets using either or both of the following options:

- **Network security groups:** 
  - *Network security groups* and *application security groups* can contain multiple inbound and outbound security rules that enable you to filter traffic to and from resources by source and destination IP address, port, and protocol. 

- **Network virtual appliances:** 
  - A *network virtual appliance* is a VM that performs a network function, such as a firewall, WAN optimization, or other network function.

## Route network traffic

Azure routes traffic between subnets, connected virtual networks, on-premises networks, and the Internet, by default. You can implement either or both of the following options to override the default routes Azure creates:

- **Route tables:** 
  - You can create custom route tables with routes that control where traffic is routed to for each subnet. 

- **Border gateway protocol (BGP) routes:** 
  - If you connect your virtual network to your on-premises network using an Azure VPN Gateway or ExpressRoute connection, you can propagate your on-premises BGP routes to your virtual networks.


## Virtual network integration for Azure services

Integrating Azure services to an Azure virtual network enables private access to the service from virtual machines or compute resources in the virtual network. 

You can integrate Azure services in your virtual network with the following options:

- Deploying **dedicated instances of the service** into a virtual network. The services can then be privately accessed within the virtual network and from on-premises networks.

- Using **Private Link** to access privately a specific instance of the service from your virtual network and from on-premises networks.

- You can also access the service using public endpoints by extending a virtual network to the service, through **service endpoints**. Service endpoints allow service resources to be secured to the virtual network.


## Comparison of Virtual Network peering and VPN Gateway.

Virtual network peering and VPN gateways both support the following connection types:

- Virtual networks in different regions.

- Virtual networks in different Azure Active Directory Tenants.

- Virtual networks in different Azure subscriptions.

- Virtual networks that uses a mix of Azure devployment models.

![](https://github.com/amarnadh19/books/blob/main/images/az_networking_2.png?)

