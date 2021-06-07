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
  - *Service endpoints* enables private IP addresses in the vnet to reach the endpoint of an Azure Service without needing a public IP 
    address on the vnet

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


## Site-to-Site and Multi-Site (IPsec/IKE VPN tunnel)

### Site-to-Site

A Site-to-Site (S2S) VPN gateway connection is a connection over IPsec/IKE (IKEv1 or IKEv2) VPN tunnel.

![](https://github.com/amarnadh19/books/blob/main/images/az_network_connect_1.png?)

VPN Gateway can be configured in active-standby mode using one public IP or in active-active mode using two public IPs.

In active-standby mode, one IPsec tunnel is active and the other tunnel is in standby.

Setting up VPN Gateway in active-active mode is recommended in which both the IPsec tunnels are simultaneously active, with data flowing through both tunnels at the same time.

### Multi-Site

This type of connection is a variation of the Site-to-Site connection. You create more than one VPN connection from your virtual network gateway, typically connecting to multiple on-premises sites.

When working with multiple connections, you must use a RouteBased VPN type.

Each virtual network can only have one VPN gateway, all connections through the gateway share the available bandwidth. This type of connection is often called a "multi-site" connection.

![](https://github.com/amarnadh19/books/blob/main/images/az_network_connect_2.png?)