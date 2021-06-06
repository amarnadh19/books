# Amazon Virtual Private Cloud Connectivity Options

## Network-to-Amazon VPC connectivity options

- **AWS Managed VPN** – Describes establishing a VPN connection from your network equipment on a remote network to AWS managed service attached to your Amazon VPC.

- **AWS Transit Gateway + VPN** – Describe establishing a VPN connection from your network equipment on a remote network to a regional network hub for Amazon VPCs, using AWS Transit Gateway.

- **AWS Direct Connect** - Describes establishing a private, logical connection from your remote network to Amazon VPC, using AWS Direct Connect.

- **AWS Direct Connect + AWS Transit Gateway** – Describes establishing a private, logical connect from your remote network to a regional network hub for Amazon VPCs, using AWS Direct Connect and AWS Transit Gateway.

- **AWS Direct Connect + Managed VPN** – Describes establishing a private, encrypted connection from your remote network to Amazon VPC, using AWS Direct Connect.

- **AWS Direct Connect + AWS Transit Gateway + VPN** – Describes establishing a private, encrypted connection from your remote network to a regional network hub for Amazon VPCs, using AWS Direct Connect and AWS Transit Gateway.

- **AWS VPN CloudHub** – Describes establishing a hub-and-spoke model for connecting remote branch offices.

- **Software Site-to-Site VPN** – Describes establishing a VPN connection from your equipment on a remote network to a user-managed software VPN appliance running inside an Amazon VPC.


## Amazon VPC-to-Amazon VPC connectivity options

- **VPC peering** – Describes connecting Amazon VPCs within and across regions using the Amazon VPC peering feature.

- **AWS Transit Gateway** – Describes connecting Amazon VPCs within and across regions using AWS Transit Gateway in a hub-and-spoke model.

- **Software Site-to-Site VPN** – Describes connecting Amazon VPCs using VPN connections established between user-managed software VPN appliances running inside of each Amazon VPC.

- **Software VPN-to-AWS Managed VPN** – Describes connecting Amazon VPCs with a VPN connection established between a user-managed software VPN appliance in one Amazon VPC and AWS managed VPN attached to the other Amazon VPC.

- **AWS Managed VPN** – Describes connecting Amazon VPCs with VPN connections between your remote network and each of your Amazon VPCs.

- **AWS PrivateLink** – Describes connecting Amazon VPCs with VPC interface endpoints and VPC endpoint services.

## Software remote access-to-Amazon VPC connectivity options

- **AWS Client VPN** – Describes connecting software remote access to Amazon VPC, leveraging AWS Client VPN.

- **Software client VPN** – Describes connecting software remote access to Amazon VPC, leveraging user-managed software VPN appliances.

## Transit VPC option

Describes establishing a global transit network on AWS using a software VPN in conjunction with an AWS-managed VPN.


## Network-to-Amazon VPC connectivity options

This section provides design patterns for connecting remote networks with your Amazon VPC environment.

VPC connectivity to remote customer networks is best achieved when using non-overlapping IP ranges for each network being connected.

### AWS Managed VPN (site to site VPN)

By default, instances that you launch into an Amazon VPC can't communicate with your own (remote) network. You can enable access to your remote network from your VPC by creating an AWS Site-to-Site VPN (Site-to-Site VPN) connection, and configuring routing to pass traffic through the connection.

#### Use case

AWS managed IPsec VPN connection over the internet to individual VPC

#### Advantages

- Reuse existing VPN equipment and processes

- Reuse existing internet connections

- AWS managed high availability VPN service

- Supports static routes or dynamic Border Gateway Protocol (BGP) peering and routing policies

#### Limitations

- Network latency, variability, and availability are dependent on internet conditions

- Customer managed endpoint is responsible for implementing redundancy and failover (if required)

- Customer device must support single-hop BGP (when leveraging BGP for dynamic routing)

Amazon VPC provides the option of creating an IPsec VPN connection between your remote networks and Amazon VPC over the internet, as shown in the following figure.

![](https://github.com/amarnadh19/books/blob/main/images/aws_network_connect_1.png?)

Figure : AWS managed VPN

Consider taking this approach when you want to take advantage of an AWS-managed VPN endpoint that includes automated redundancy and failover built into the AWS side of the VPN connection.

The virtual private gateway also supports and encourages multiple user gateway connections so that you can implement redundancy and failover on your side of the VPN connection, as shown in the following figure.

![](https://github.com/amarnadh19/books/blob/main/images/aws_network_connect_2.png?)

Figure: AWS Managed VPN multiple User Gateways

### Site-to-Site VPN Components

A Site-to-Site VPN connection offers two VPN tunnels between a virtual private gateway or a transit gateway on the AWS side, and a customer gateway (which represents a VPN device) on the remote (on-premises) side.

#### Virtual private gateway

A virtual private gateway is the VPN concentrator on the Amazon side of the Site-to-Site VPN connection. You create a virtual private gateway and attach it to the VPC from which you want to create the Site-to-Site VPN connection.

![](https://github.com/amarnadh19/books/blob/main/images/aws_network_connect_3.png?)

#### Transit gateway

A transit gateway is a transit hub that you can use to interconnect your virtual private clouds (VPC) and on-premises networks.

![](https://github.com/amarnadh19/books/blob/main/images/aws_network_connect_4.png?)


#### Customer gateway device

A customer gateway device is a physical device or software application on your side of the Site-to-Site VPN connection.

#### Customer gateway

A customer gateway is a resource that you create in AWS that represents the customer gateway device in your on-premises network.

