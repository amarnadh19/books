# Elastic load balancing

Elastic Load balancing helps to balance traffic between AWS services.

It scales automatically to absorb the load.

Customers can enable Elastic Load Balancing within a single or multiple Availability Zones for more consistent application performance.

Elastic Load Balancing automatically distributes incoming application traffic across multiple Amazon EC2 instances.

Elastic Load Balancing can also be used in an Amazon Virtual Private Cloud (“VPC”) to distribute traffic between application tiers in a virtual network that you define.

ELB provides greater levels of Fault Tolerance.

It also detects unhealthy instances and automatically reroutes trafic to healthy instances until unhealthy are restored.


## Load balancer benefits

You can add and remove compute resources from your load balancer as your needs change, without disrupting the overall flow of requests to your applications.

## Features of Elastic Load Balancing

Elastic Load Balancing supports the following load balancers: 

- Application Load Balancers
- Network Load Balancers
- Gateway Load Balancers
- Classic Load Balancers


## How Elastic Load Balancing works

You configure your load balancer to accept incoming traffic by specifying one or more *listeners*.

**A Listener** is a process that checks for connection requests. It is configured with a protocol and port number for connections from clients to the load balancer. Likewise, it is configured with a protocol and port number for connections from the load balancer to the targets.


	Note:

	There is a key difference in how the load balancer types are configured. With Application Load Balancers, Network Load Balancers, and Gateway Load Balancers, you register targets in target groups, and route traffic to the target groups. With Classic Load Balancers, you register instances with the load balancer.


## Availability Zones and load balancer nodes

By using Multi AZ ELB, If one Availability Zone becomes unavailable or has no healthy targets, the load balancer can route traffic to the healthy targets in another Availability Zone.

### Cross-zone load balancing

When cross-zone load balancing is enabled, *each load balancer node distributes traffic across the registered targets in all enabled Availability Zones.*

When cross-zone load balancing is disabled, each load balancer node distributes traffic only across the registered targets in its Availability Zone.

The following diagrams demonstrate the effect of cross-zone load balancing. 

There are two enabled Availability Zones, with two targets in Availability Zone A and eight targets in Availability Zone B. Clients send requests, and Amazon Route 53 responds to each request with the IP address of one of the load balancer nodes. This distributes traffic such that each load balancer node receives 50% of the traffic from the clients. Each load balancer node distributes its share of the traffic across the registered targets in its scope.

![](https://github.com/amarnadh19/books/blob/main/images/aws_elb_1.png?)

If cross-zone load balancing is disabled:

Each of the two targets in Availability Zone A receives 25% of the traffic.
Each of the eight targets in Availability Zone B receives 6.25% of the traffic.
This is because each load balancer node can route its 50% of the client traffic only to targets in its Availability Zone.

If cross-zone load balancing is enabled, each of the 10 targets receives 10% of the traffic. This is because each load balancer node can route its 50% of the client traffic to all 10 targets.

![](https://github.com/amarnadh19/books/blob/main/images/aws_elb_2.png?)

With Application Load Balancers, cross-zone load balancing is always enabled.

With Network Load Balancers and Gateway Load Balancers, cross-zone load balancing is disabled by default. After you create the load balancer, you can enable or disable cross-zone load balancing at any time.

When you create a Classic Load Balancer, the default for cross-zone load balancing depends on how you create the load balancer. 


