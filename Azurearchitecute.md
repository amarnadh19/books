# Azure Well-Architected Framework Pillars


Azure has five pillars

	1) Cost Optimization
	2) Operational excellence
	3) Performance efficiency
	4) Reliability
	5) Security

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_1.png?)

#### Cost Optimization:

Design cloud for cost effective for operations and development.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_2.png?)

#### Operational Excellence:

By Taking advantange of modern development practices such as devops you can enable faster development and deployment cycles. You should have good monitoring arch in place so that you can detect failurs and problems before they happen or min time before cutomer notice it.


#### Performance Efficiency:

For architecture to perform well and scalable, it should properly match resources capacity to demand. Generally cloud devices use dynamic scaling based on activity.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_3.png?)

#### Reliability:

A successfull cloud environment is designed in a way that anticipates failures at all levels.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_4.png?)


#### Security:

We need to secure data from attacks from unknown hackers. The integrity of your data should be protected too, through tools like encryption.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_5.png?)


## General design Principles

#### Enable architectural evolution:

No architecture is static. Allow for the evolution of your architecture by taking advantage of new services, tools and technologies when they are available.

#### Use data to make decisions:

Collect data analyze it, and use it to make decisions surrounding your architecture. From cost data, to Performance to user load, using data will guide you to make the right choices in your environment.

#### Educate and enable:

Cloud technology evolves quickly. Educate your development, operations and business teams to help them make the right decisions and build solutions to solve business problems.

#### Automate:

Automation of manual activities reduces operational cost, minimizes error introduced by manual steps and provides consistency between environments.


## Design choices

In an ideal architecutre, you would build the most secure high-performance highly available, and efficient environment possible.

To build an environment with the highest level of all these pillars, there's a cost. That cost might be in money, time to deliver, or operational agility. Every organization will have different priorities that will affect the design choices that are made in each pillar. As you design your architecture, you'll need to determine which trade-offs are acceptable, and which are not.

When you're building an Azure architecture, there are many considerations to keep in mind. You want your architecture to be secure, scalable, available, and recoverable. To make that possible, you'll have to make decisions based on cost, organizational priorities, and risk.

***

## Cost Optimization

### What is cost Optimization

Cost optimization is ensuring that the money your organization spends is being used to maximum effect.

Cloud services provide computing as a utility.

Technologies in the cloud are provided under a service model, to be consumed on demand.

When an organization decides to own infrastructure, it buys equipment that goes onto the balance sheet as assets. Because a capital investment was made, accountants categorize this transaction as a capital expense **(CapEx)**.

Cloud services, on the other hand, are categorized as an operating expense **(OpEx)**, because of their consumption model.

When an organization adopts a cloud platform, it must shift away from CapEx-orented budgeting toward OpEx.

To optimize costs in your organization's architecture, you can use several principles.


#### Plan and estimate costs

For any cloud project, whether it is the development of a new application or the migration of an entire datacenter, it is important to get an estimate of your costs.

This estimate involves identifying any current resources to move or redevelop, understanding business objectives that might affect sizing, and selecting the appropriate services for the project.

With the requirements identified, you can use cost estimation tools to provide a more concise estimate of the resources that would be required.


#### Provision with Optimization

Provisioning services that are optimized for cost from the outset can reduce your work effort in the future.

For example, you should ensure that you are selecting the appropriate service level for your workload, and take advantage of services that let you adjust the service level. You should also use discounts when they are available, such as reserved instances and bring-your-own license offers.

Where possible you want to move from IaaS to PaaS. PaaS services typically cost less than IaaS, and they typically reduce your operational costs. Not all applications can be moved to PaaS, but with the cost savings that PaaS services provide, it is worth considering.


#### Use monitoring and analytics to gain cost insights

If you are not monitoring your spending, you do not know what you can save. Take advantage of cost management tools and regularly review billing statements to better understanding where money is being spent.

***

## Operational Excellence

### What is Operational Excellence?

It ensures that you have full visibility into how your application is running, and ensuring the best experience for your users. Operational excellence includes making your development and release practices more agile, which allows your business to quickly adjust to changes.

By improving operational capabilities, you can have faster development and release cycles and a better experience ofr users of your application.


#### Design, Build and orchestrate with modern practices

Modern architectures should be designed twith DevOps and continuous integration in mind.

A Modern Architectures will give you the abililty to automate deployments by using infrastructure as code, automate application testing and build new environments as needed.


#### Use Monitoring and analytics to gain operational insights.

By creating an effective system for monitoring what is going on in your architecute, you can ensure that you will know when something is not right before your users are affected.

Operationally, it is important to have a robust monitoring strategy. This helps you identify areas of waste, troubleshoot issues, and optimize the performance of your application.

A multilayered approach is essential.

Gathering data points from a components at every layer will help alert you when values are outside acceptable ranges and help you track spending over time.


#### Use automation to reduce effort and error.

You should automate as much of your architecute as pssible. The human element is costly, injecting time and error into operational activities.

This increased time and error will result in increased operational costs.


#### Test

You should include testing in your application deployment and your ongoing operations. A good testing strategy will help you identify issues in your application before it is deployed, and ensure that dependent services can properly communicate with your application.

A good testing strategy can also help identify performance issues and potential security vulnerabilites in both pre-production and production deployments.

A robust testing plan can uncover issues with infrastructuredeployments that can affect the user experience and testing will help you provide a great experinece for your users.

***

## Performance Efficiency

### What is Performance efficiency

Performance efficency is matching the resources that are available to an application with the demand that is receiving.

### Scale up and Scale out

Compute resources can be scaled in two directions:

#### Scaling up is adding more resources to a single instance.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_6.png?)

#### Scaling out is adding more instances.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_7.png?)

Scaling up is concerned with adding more resources, such as CPU or memory, to a single instance. This instance might be a virtual machine or a PaaS service.

Scaling out is concerned with adding more instances to a service. They can be virtual machines or PaaS services. Instead of adding more capacity by making a single instance more powerful, we add capacity by increasing the total number of instances.

In both types of scaling, resources can be reduced, which brings cost optimization into the picture.

*Autoscaling* is the process of dynamically allocating resources to match performance requirements.


### Optimize network performance

When you're optimizing for performance, you'll look at network and storage performance to ensure that their levels are within acceptable limits. These performance levels can affect the response time of your application. Selecting the right networking and storage technologies for your architecture will help you ensure that you're providing the best experience for your consumers.

**Adding a messaging layer between services can have a benefit to performance and scalability.** A messaging layer creates a buffer so that requests can continue to flow in without error if the receiving application can't keep up. As the application works through the requests, they'll be answered in the order in which they were received.


### Optimize storage performance

In many large-scale solutions, data is divided into separate partitions that can be managed and accessed separately. The partitioning strategy must be chosen carefully to maximize the benefits while minimizing adverse effects. Partitioning can help improve scalability, reduce contention, and optimize performance.

Use caching in your architecture to help improve performance. Caching is a mechanism to store frequently used data or assets (webpages, images) for faster retrieval. You can use caching at different layers of your application. You can use caching between your application servers and a database in order to decrease data retrieval times.

You can also use caching between your users and your web servers, by placing static content closer to users and decreasing the time it takes to return webpages to the users. This has a secondary effect of offloading requests from your database or web servers, increasing the performance for other requests.


### Identify performance bottlenecks in your application

Distributed applications and services running in the cloud are complex pieces of software that comprise many moving parts. In a production environment, it's important to be able to track the way in which users utilize your system, trace resource utilization, and generally monitor the health and performance of your system. You can use this information as a diagnostic aid to detect and correct issues. You can also use this information to help spot potential problems and prevent them from occurring.

Look across all layers of your application and identify and remediate performance bottlenecks. These bottlenecks might be poor memory handling in your application, or even the process of adding indexes into your database. It might be an iterative process as you relieve one bottleneck and then uncover another that you were unaware of.

***

## Reliability

### What is reliability?

Designing for reliability includes maintaining uptime through small-scale incidents and temporary conditions like partial network outages.

You can ensure that your application can handle localized failures by integrating high availability into each component of the application and eliminating single points of failure. Such a design also minimizes the impact of infrastructure maintenance. High-availability designs typically aim to eliminate the impact of incidents quickly and automatically, and to ensure that the system can continue to process requests with little to no impact.

Designing for reliability also focuses on recovery from data loss and from larger-scale disasters. Recovery from these types of incidents often involves active intervention, though automated recovery steps can reduce the time needed to recover. These types of incidents might result in some amount of downtime or permanently lost data. Disaster recovery is as much about careful planning as it is about execution.

Architecting for reliability ensures that your application can meet the commitments you make to your customers. This includes ensuring that your systems are available to end users and can recover from any failures.

Including high availability and recoverability in the design of your architecture protects your business from financial losses that result from downtime and lost data. They ensure that your reputation isn't negatively affected by a loss of trust from your customers.


### Build a highly available architecture

For availability, identify the service-level agreement (SLA) you're committing to. Examine the potential high-availability capabilities of your application relative to your SLA, and identify where you have proper coverage and where you'll need to make improvements. Your goal is to add redundancy to components of the architecture so that you're less likely to experience an outage.

Examples of high-availability design components include clustering and load balancing:

- Clustering replaces a single VM with a set of coordinated VMs. When one VM fails or becomes unreachable, services can fail over to another one that can service the requests.

- Load balancing spreads requests across many instances of a service, detecting failed instances and preventing requests from being routed to them.


### Build an architecture that can recover from failure

For recoverability, you should perform an analysis that examines your possible data loss and major downtime scenarios. Your analysis should include an exploration of recovery strategies and the cost/benefit tradeoff for each

- **Recovery point objective (RPO)**: The maximum duration of acceptable data loss. RPO is measured in units of time, not volume. Examples are "30 minutes of data," "four hours of data," and so on. RPO is about limiting and recovering from data loss, not data theft.

- **Recovery time objective (RTO)**: The maximum duration of acceptable downtime, where "downtime" is defined by your specification. For example, if the acceptable downtime duration is eight hours in the event of a disaster, then your RTO is eight hours.

With RPO and RTO defined, you can design backup, restore, replication, and recovery capabilities into your architecture to meet these objectives.

- Every cloud provider offers a suite of services and features that you can use to improve your application's availability and recoverability. When possible, use existing services and best practices, and try to resist creating your own.

- Hard drives can fail, datacenters can become unreachable, and hackers can attack. It's important that you maintain a good reputation with your customers by using availability and recoverability. Availability focuses on maintaining uptime through conditions like network outages, and recoverability focuses on retrieving data after a disaster.

***

## Security

### what is security?

Security is ultimately about protecting the data that your organization uses, stores, and transmits. The data that your organization stores or handles is at the heart of your securable assets.

For instance, in the healthcare industry in the United States, there's a law called the Health Insurance Portability and Accountability Act (HIPAA). In the financial industry, the Payment Card Industry Data Security Standard is concerned with the handling of credit card data. In Europe, the General Data Protection Regulation (GDPR) lays out the rules of how personal data is protected, and defines individuals' rights related to stored data.


### Defense in Depth

A multilayered approach to securing your environment will increase the security posture of your environment. Commonly known as defense in depth, we can break down the layers as follows:

- Data
- Applications
- VM/compute
- Networking
- Perimeter
- Policies and access
- Physical security

Each layer focuses on a different area where attacks can happen and creates a depth of protection, if one layer fails or is bypassed by an attacker. If we were to focus on just one layer, an attacker would have unfettered access to your environment if they got through this layer.

Each layer will have different security controls, technologies, and capabilities that will apply. When you're identifying the protections to put in place, cost is often of concern. You'll need to balance cost with business requirements and overall risk to the business.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_8.png?)

No single security system, control, or technology will fully protect your architecture. Security is more than just technology; it's also about people and processes. Creating an environment that looks holistically at security, and making it a requirement by default, will help ensure that your organization is as secure as possible.

### Protect from common attacks

At each layer, there are some common attacks that you'll want to protect against. The following list isn't all-inclusive, but it can give you an idea of how each layer can be attacked and what types of protections you might need.

- **Data layer:** Exposing an encryption key or using weak encryption can leave your data vulnerable if unauthorized access occurs.

- **Application layer:** Malicious code injection and execution are the hallmarks of application-layer attacks. Common attacks include SQL injection and cross-site scripting (XSS).

- **VM/compute layer:** Malware is a common method of attacking an environment, which involves executing malicious code to compromise a system. After malware is present on a system, further attacks that lead to credential exposure and lateral movement throughout the environment can occur.

- **Networking layer:** Unnecessary open ports to the internet are a common method of attack. These might include leaving SSH or RDP open to virtual machines. When these protocols are open, they can allow brute-force attacks against your systems as attackers attempt to gain access.

- **Perimeter layer:** Denial-of-service (DoS) attacks often happen at this layer. These attacks try to overwhelm network resources, forcing them to go offline or making them incapable of responding to legitimate requests.

- **Policies and access layer:** This layer is where authentication occurs for your application. This layer might include modern authentication protocols such as OpenID Connect, OAuth, or Kerberos-based authentication such as Active Directory. The exposure of credentials is a risk at this layer, and it's important to limit the permissions of identities. We also want to have monitoring in place to look for possible compromised accounts, such as logins coming from unusual places.

- **Physical layer:** Unauthorized access to facilities through methods such as door drafting and theft of security badges can happen at this layer.


### Shared security responsibility

Revisiting the model of shared responsibility, we can reframe this in the context of security. Depending on the type of service you select, some security protections will be built in to the service, while others will remain your responsibility.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_9.png?)


***

# Microsoft Azure Well-Architected Framework - Cost optimization


