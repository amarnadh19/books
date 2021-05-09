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

## Plan and estimate your Azure costs


Whether your organization wants to build a new application on Azure, or you're looking to move an entire datacenter to the cloud, estimating costs is a key part of your planning process to ensure a successful project.

Proper planning is incredibly important to any cloud project. Let's look at what you need to consider.

### Capture requirements

Before you start any cloud project, take time to plan properly. That's especially important when you're considering costs.

Start by identifying the stakeholders for the project. This should include the business teams that are driving the organizational outcomes.

Identify the business and technical requirements of your project:

- Business requirements might be an API to enable partner communications or a reporting interface for the accounting department to view financial transactions.

- Technical requirements might be the ability to store relational data, or the ability for users to use a personal identity to access applications.

Both of these requirements will affect the overall cost of the project. They'll also influence your selection of services.

After you have identified your requirements, you'll want to define the workloads that are in scope to use cloud services, and identify the services and resources you'll use.

When you have listed all of the requirements, services, and resources for your project, you can begin to estimate your costs.


### Estimating the cost

With your list of services captured, you can use the ***Azure Pricing Calculator*** to create estimates of the cost of your application.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_10.png?)


As part of your cost estimation, it's also important to understand the subscription and billing models that are available on Azure. Two of the most common models are pay-as-you-go and enterprise agreement:

- Pay-as-you-go subscriptions give you the flexibility to purchase and use the services you need, with the advantage of having no up-front commitments.

- Enterprise agreements enable organizations to take advantage of discounts through up-front commitments. These agreements enable organizations to centralize their Azure costs and billing. They can include other Microsoft services such as Microsoft 365.

There are additional billing models. Each gives you access to the full suite of Azure services with the flexibility to purchase only what you need, when you need it.

Evolving your architecture can reduce resources costs, such as moving from virtual machines to app services. It can also reduce operational costs by requiring less downtime for maintenance.


### Organize resources for cost awareness

It's also important to set up an organizational framework to enable the control, reporting, and attribution of costs throughout your environment.

Use Azure Policy to create limitations for the size or tier of resources that can be provisioned.

Enable your users to view reports and billing as needed by creating roles that allow them to view services such as Azure Cost Management. Enabling your users to view costs will help them see the impact of their business decisions. It also provides for transparency across the organization with respect to cloud resource costs.

Organize your resources into resource groups or subscriptions. They can serve as boundaries for projects, business units, or services. You can also use Azure Policy to enforce the tagging of resources. Subscriptions, resource groups, and tags are exposed in billing reports. These reports will enable you to account for the usage of resources by product, business unit, or project.


### Budget for education

Educating your engineers, developers, and users is an important piece of a successful cloud project.


## Provision with optimization

When provisioning resources, you'd ideally make them as efficient as possible from the start.

### Select appropriate service tiers and sizes

When you're provisioning resources on the cloud, selecting the right SKU or tier will have a direct impact on the capabilities, capacity, and performance of the Azure service. This selection is tied directly to cost.

There is a wide variety of virtual machine types to choose from when you're provisioning for VM-based workloads. Each VM SKU comes with an assigned amount of CPU, memory, and storage. Assess the resource requirements for your workload, and select the VM SKU that most closely matches your needs.

Provisioning VM sizes can often be challenging. You might be deploying for your maximum workload, even though your application needs that capacity for only a portion of its running time. Choosing a VM size is not a permanent decision. **You can modify your VM size at any time, but in most cases it will require a restart of your VM.**


### Pay only for consumption

Many cloud services provide a consumption billing model. With consumption models, you pay for only the amount of transactions, CPU time, or run time of your application. This can bring cost savings and efficiency to your application, because you aren't paying for the resources to run your application when it's not being used. Let's look at a few examples of Azure services that have a consumption cost model:

- **Azure Functions** is an event-driven, serverless compute platform that provides a consumption plan. When you're using the consumption plan, you're charged for compute resources only when your functions are running. Billing is based on the number of executions, the length of time running, and the amount of memory used. As an added benefit, your function scales automatically. Instances of the Azure Functions host are dynamically added and removed based on the number of incoming events. Function execution times out after a configurable period of time.

- **Azure Logic Apps** is a service that helps you create automated, integration workflows in the cloud. Logic Apps provides a consumption tier where you only pay per execution of a connector.

- **Azure SQL Database** is service that enables you to store relational data in the cloud. Azure SQL Database has a serverless tier where you can reduce your costs by pausing the database when it's not in use. Azure SQL Database serverless is price-performance optimized for single databases with intermittent, unpredictable usage patterns that can afford some delay in compute warm-up after idle usage periods.

- **Azure API Management** is a service that provides centralized API administration, proxy, and deployment. API Management has a consumption tier that bills per execution, and will scale out automatically as requests change over time. The consumption tier enables the service to be used in a serverless fashion, with instant provisioning, automated scaling, built-in high availability, and pay-per-action pricing.


### Use spot instances for low-priority workloads

You can use spot VMs to take advantage of unused capacity on Azure at a significant cost savings. At any point when Azure needs the capacity back, the Azure infrastructure will evict spot VMs. Spot VMs are great for workloads that can handle interruptions like batch processing jobs, development/test environments, and large compute workloads.


### Take advantage of reserved instances

Azure reservations help you save money by committing to one-year or three-year plans for multiple products. Committing to one of these plans enables you to get a discount on the resources you use. Reservations can reduce your resource costs up to 72 percent on pay-as-you-go prices. Reservations provide a billing discount and don't affect the runtime state of your resources. After you purchase a reservation, the discount automatically applies to matching resources.

Reservations are available for services such as:

- Windows and Linux virtual machines
- Azure SQL Database
- Azure Cosmos DB
- Azure Synapse Analytics
- Azure Storage


### Use managed services when possible

Whenever possible, take advantage of combining lower resource costs and lower operational costs by using managed services. These services come with lower operational costs because you don't need to patch and manage the underlying infrastructure and services. Deploying applications on VMs comes with the administration and maintenance of the operating system, as well as any layered software.

Azure SQL Database is a great example of a managed service. You can deploy a single or pooled database, or a managed instance, and each of these is fully managed. You don't need to patch the underlying database software, and operational items like backup are built in and provided for you.

Azure App Service is another example of a managed service that is designed to host web applications. Rather than deploying and managing VMs to host your web applications, you can deploy your applications directly to App Service, and dramatically reduce the amount of effort that is required to maintain infrastructure.


## Use monitoring and analytics to gain cost insights

You've deployed your application by using infrastructure and services that are as cost-effective as possible. But what do you do when your business, customer demand, or application changes?


### Track your cloud spend

To make intelligent decisions, you need data. By analyzing where your money is going, you can compare your costs to your utilization to discover where you might have waste within your environment.

An export of your billing data is available at any time. By using your billing data, you can track where your costs are going and how they're allocated across your resources. One challenge for you is that the billing data shows your costs but not your utilization. You'll have data that indicates you're paying for a large VM, but how much are you actually using it?

**Azure Cost Management** gives you insights into where your spend is going, as well as underutilized resources. Azure Cost Management tracks your total spend, cost by service, and cost over time. You can drill down into resource types and instances. You can also break down your costs by organization or cost center by tagging resources with those categories.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_11.png?)

Azure Advisor also has a cost component that:

- Recommends VM resizing when necessary.
- Identifies unused Azure ExpressRoute circuits and idle virtual network gateways.
- Advises when to consider buying reserved instances because that might be more cost-effective than using pay-as-you-go instances.

Azure Advisor makes additional recommendations in the areas of performance, high availability, and security.

The important part is to take time to review your spend, and evaluate where your money is going. Effective analysis will help you identify areas of inefficiency, and ensure you're operating as cost-effectively as possible.


### Conduct cost reviews

After you have your Azure services running, you should regularly check your costs to track your Azure spending. You can use cost analysis to understand where the costs originated for your Azure usage.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_12.png?)

Take time as an organization to regularly meet and review billing and expenditures that are related to cloud services. Review the respective expenditures with the technical and business stakeholders for each application. This brings increased visibility to the costs that are associated with an application, and the decisions made from a cost perspective.


### Respond to cost alerts

One of the key features of Azure Cost Management is the ability to configure alerts that are based on spending. These alerts can provide immediate visibility into spending that might be exceeding your budget. You can then take steps to address these costs. There are three types of cost alerts:

- **Budget alerts** notify you when spending, based on usage or cost, reaches or exceeds the amount defined in the *alert* condition of the budget. Budgets in **Azure Cost Management** help you plan for and drive organizational accountability.

  - With budgets, you can account for the Azure services that you consume or subscribe to during a specific period. They help you to proactively inform others about their spending, and to monitor how spending progresses over time. When the budget thresholds that you've created are exceeded, alerts can be sent to the appropriate teams. You can set budgets at varying levels, from resource groups to subscriptions to enterprise agreements.

- **Credit alerts** notify you when your Azure credit monetary commitments are consumed. Monetary commitments are for organizations with enterprise agreements.

- **Department spending quota alerts** notify you when department spending reaches a fixed threshold of the quota. You configure spending quotas in the Azure Enterprise Agreement portal. When a threshold is met, an email is sent to department owners and a notification appears in cost alerts.


### Report anomalies

When an anomaly in spending is identified through your data collection, cost reviews, or cost alerts, you should report it to the necessary stakeholders.


## Maximize efficiency of cloud spend

### How the cloud changes your expenses

One of the differences between the public cloud and on-premises infrastructure is how you pay for the services that you use.

In an on-premises datacenter, hardware procurement is a long process. Physical hardware is sized for maximum capacity. Some of the costs, such as computer power and storage space, can be hidden from the business units that are consuming those resources. Purchasing physical infrastructure ties up investments in long-term assets, which hinders your ability to be agile with your resources.

Shifting to the cloud replaces the burgeoning costs of maintaining physical infrastructure with a pay-for-what-you-use cost model. You no longer need to tie up investments in physical assets. If your resource requirements change, you can respond by adding, moving, or removing resources.

Cloud infrastructure can handle fluctuating resource usage scenarios. Resources that have significant periods of inactivity can be shut down when not in use, and then not incur any cost at all.


## Optimize IaaS costs

The compute costs are typically your largest expense, followed by storage costs.

Let's take a look at best practices to reduce your compute and storage costs.

### Compute

A few options are available to achieve cost savings for virtual machines:

- Choose a smaller size for the virtual machine instance.
- Reduce the number of hours a virtual machine runs.
- Use discounts for the compute costs.

#### Rightsize virtual machines

Rightsizing a virtual machine is the process of matching virtual machine sizes with the respective requirements for resource demand. If a VM is running 25 percent idle, reducing the size of the VM will immediately reduce your cost. Virtual machine costs are linear within an instance family; each next size larger will double your cost. Conversely, reducing a VM by a single instance size will reduce your cost by half.

The following illustration shows a 50 percent savings achieved by moving one size down within the same series.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_13.png?)

Azure Advisor identifies which virtual machines are underutilized. Azure Advisor monitors your virtual machine usage for 14 days, and then it identifies any underutilized virtual machines. Virtual machines with a CPU utilization of 5 percent or less, and network usage of 7 MB or less, for four or more days are considered underutilized.

#### Implement shutdown schedules for virtual machines

If you have VM workloads that are used only periodically, but are running continuously, you're wasting money. These VMs can be shut down when they're not in use, which saves your compute costs while the VM is deallocated. For example, a development environment is a good candidate for shutdown during your organization's off hours because development generally happens only during business hours.

You have several options to deallocate a VM. For example:

- You can use Azure Automation to run your VMs only during times that your workloads require.
- You can use the auto-shutdown feature on a virtual machine to schedule a one-off automated shutdown.
- You can manually stop a VM in the Azure portal.

You should always use the Azure controls to stop your VMs. Shutting down the OS from inside a VM does not deallocate its Azure resource, so you'll continue to accrue costs.


#### Apply compute cost discounts

Azure Hybrid Benefit offers an additional way to optimize the costs of your Windows Server and SQL Server instances. It enables you to use your licenses for your on-premises computers running Windows Server or SQL Server with Software Assurance as a discount toward the compute cost of these VMs. You can then reduce or eliminate the costs for Windows Server and SQL Server on enabled instances.

Azure Reserved Virtual Machine Instances (Azure RI) enables you to purchase compute capacity for a one-year or three-year commitment. It offers you significant savings - up to 72 percent - when compared to pay-as-you-go compute resources.

The following illustration shows savings achieved when you combine your on-premises licenses with Azure Hybrid Benefit. It also shows savings achieved when you combine your on-premises licenses with both Azure Reserved Virtual Machine Instances and Azure Hybrid Benefit.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_14.png?)


#### Cost optimization for VM disk storage

For workloads that don't require high reliability and performance disks, you can use the reduced-cost standard storage. For example, you might choose to use standard storage for your development and test environments that are not required to be an identical match for your production workloads.


Disks that aren't associated with a VM still incur storage costs, so you should make sure you don't have any orphaned disks remaining in your environment.

If you've removed a VM but not its associated disks, you can reduce your storage costs by identifying and removing these orphaned disks from your environment.

You should also make sure that you don't have any orphaned snapshots remaining in your environment. Pricing for snapshots is lower than pricing for the disks themselves, but it's still a good practice to eliminate costs for unnecessary resources.


## Optimize PaaS costs

Platform as a service (PaaS) services are typically optimized for costs over IaaS services. But there are opportunities to identify waste and optimize for minimal costs in your PaaS services as well. 

### Optimize Azure SQL Database costs

When creating an Azure SQL database, you have to select a server and decide on a performance tier. Each tier provides a performance level either in database transaction units (DTUs) or virtual cores (vCores).

SQL Database elastic pools are a simple, cost-effective solution for managing and scaling several databases that have varying and unpredictable usage demands.

The databases in an elastic pool are on a single Azure SQL Database server, and share a set number of resources at a set price. Pools are well suited for a large number of databases with specific utilization patterns. For a given database, this pattern is characterized by low average utilization, with relatively infrequent utilization spikes.

The more databases you can add to a pool, the greater your savings become. The following illustration shows the capabilities of the three types of elastic database pools:

- Basic autoscales up to 5 eDTUs per database.
- Standard autoscales up to 100 eDTUs per database.
- Premium autoscales up to 1,000 eDTUs per database.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_15.png?)

Elastic pools are a great way to spread costs across multiple databases. They can make a significant impact on reducing your Azure SQL Database costs.

### Optimize Blob Storage costs

Blob Storage is a cost-effective way to store data. But as the amount of data grows, your bill can benefit from optimizing how the data is stored.

Azure Storage offers three tiers for blob object storage:

- **Hot access tier:** Highest storage costs but lowest access costs. This tier is optimized for storing data that's accessed often.

- **Cool access tier:** Lower storage costs and higher access costs compared to hot storage. This tier is optimized for storing data that's infrequently accessed and stored for at least 30 days.

- **Archive access tier:** Lowest storage cost and highest data retrieval costs compared to hot and cool storage. This tier is optimized for storing data that is rarely accessed and stored for at least 180 days, with flexible latency requirements (for example, several hours of retrieval latency).


### Consumption pricing models

Moving to PaaS services can take the pay-as-you-go model even further into a true consumption pricing model. Services such as Azure Functions have the ability to use consumption plans.

When you're using a consumption plan, instances of the Azure Functions host are dynamically added and removed based on the number of incoming events. This serverless plan scales automatically, and you're charged for compute resources only when your functions are running. On a consumption plan, a function execution times out after a configurable period of time. Billing is based on the number of executions, the length of execution time, and the amount of memory used. Billing is aggregated across all functions within a function app.

Moving to services that use a consumption pricing model can bring a new approach to cost savings into your architecture.

