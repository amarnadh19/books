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

***

# Microsoft Azure Well-Architected Framework - Operational excellence

## Design, build, and orchestrate with modern practices

Development and operational practices have evolved over the years to become more seamless and integrated


### DevOps

DevOps is the union of people, processes, and products to enable continuous delivery of value to end users. DevOps focuses on bringing the development and operations functions together, and breaking down the existing barriers between them.

There are several services and tools that are available from Microsoft to help an organization adopt and develop DevOps practices. Azure DevOps is a suite of products and tools that teams adopting DevOps practices can use to plan, develop, deliver, and operate their solutions.

Azure Boards is a part of Azure DevOps that helps teams plan and track work. Azure Boards has modern agile tools like Kanban boards, backlogs, dashboards and scrum boards to enable your team to have greater visibility into the work that is planned, and what has been delivered.

### Continuous Integration and Continuous Delivery (CI/CD)

Continuous Integration (CI) is the practice of building and testing code every time a team member commits changes to version control. CI encourages developers to share their code and unit tests by merging their changes into a shared version control repository after every small task completion. Committing code triggers an automated build system to grab the latest code from the shared repository, and then build, test, and validate the full master branch.

Continuous Delivery (CD) is the process to build, test, configure and deploy from a build environment to a production environment. Multiple testing or staging environments create a release pipeline to automate the creation of infrastructure and deployment of a new build. Successive environments support progressively longer-running activities of integration, load, and user acceptance testing.

Continuous integration and continuous delivery are often combined into a single pipeline known as CI/CD. Continuous integration starts the continuous delivery process, and the CI/CD pipeline stages changes from each successive environment to the next upon successful completion of the tests that are defined at each stage.

Azure Pipelines is a cloud service that you can use to automatically build and test your code project and make it available to others. It works with just about any language or project type, and integrates with GitHub, GitHub Enterprise, Azure Repos, and other version control systems. Azure Pipelines combines continuous integration (CI) and continuous delivery (CD) to constantly and consistently test and build your code and ship it to any target.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_16.jpg?)


### Microservices

A microservices architecture consists of services that are small, independent, and loosely coupled. Each service can be deployed and scaled independently.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_17.png?)

A microservice is small enough that a single, small team of developers can write and maintain it. Because services can be deployed independently, a team can update an existing service without rebuilding and redeploying the entire application.


### Environment consistency

A key piece of ensuring that you can develop and deploy applications with confidence is by ensuring that your environments are consistent between development, test, and production. As your CI/CD processes move your code through your environments, any variation risks introducing areas where testing can fail or overlook defects.


## Use monitoring and analytics to gain operational insights

Monitoring is the act of collecting and analyzing data to determine the performance, health, and availability of your business applications, and the resources on which they depend. An effective monitoring strategy helps you focus on the health of your application.  It also helps you increase your uptime by proactively notifying you of critical issues, so that you can resolve them before they become problems.

When it comes to monitoring and analytics on Azure, we can bundle services into three specific areas of focus:

- Core monitoring
- Deep infrastructure monitoring
- Deep application monitoring

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_18.png?)


## Core Monitoring

Core monitoring provides fundamental, required monitoring across Azure resources. When we talk about fundamental monitoring, you can think of this as monitoring what is happening with your resources at the Azure platform level. This area of focus gives you insight into things like the health of the Azure platform, changes being made to your resources, and performance metrics. Using services from this area gives you the ability to monitor the basic pieces you need to keep your application running.

Azure provides services to give you visibility into four key core monitoring areas: activity logging, the health of services, metrics and diagnostics, and recommendations on best practices.

These services are built in to Azure and take little to no configuration to enable and set up. Let's take a closer look at each of these services.


### Activity logging (Activity logging)

Activity logging is an incredibly important source of information about what is happening with your resources at the Azure platform level. Every change that is submitted to the Azure platform is tracked in the Azure Activity Log, which gives you the ability to trace any action that is taken on your resources. The Activity Log will contain detailed information on activities to help you answer questions like:

- Who has attached a disk to this virtual machine?
- When was this machine shut down?
- Who changed the load balancer configuration?
- Why did the autoscale operation on my virtual machine scale set fail?

Using Activity Log to answer these types of questions will help you troubleshoot issues, track changes, and provide auditing of what's happening in your Azure environment. Activity Log data is only retained for 90 days, although you can archive your data to a storage account, or you can send your data to Azure Log Analytics for longer retention and further analysis.


### Health of cloud services (Service Health)

At some point, any system can have issues, and that's true for Azure services as well.  Staying informed of the health of Azure services will help you understand if and when an issue that is impacting an Azure service is impacting your environment. What may seem like a localized issue could be the result of a more widespread issue, and Azure Service Health provides this insight. Azure Service Health identifies any issues with Azure services that might affect your application. Service Health also helps you plan for scheduled maintenance.


### Metrics and diagnostics (Azure Monitor)

The ability to view metrics and diagnostic information is critical for troubleshooting performance issues and staying notified when something goes wrong. To provide this visibility, Azure services have a common way of showing health, metric, or diagnostic information. Azure Monitor enables core monitoring for Azure services by allowing the collection, aggregation, and visualization of metrics, activity logs, and diagnostic logs.

Metrics are available that provide performance statistics for different resources, and even the operating system inside a virtual machine. You can view this data with one of the explorers in the Azure portal, and create alerts based on these metrics. Azure Monitor provides a fast metrics pipeline, so you should use it for time-critical alerts and notifications.


### Recommendations on best practices (Azure Advisor)

Azure Advisor can help by keeping an eye out for potential performance, cost, high availability, or security issues within your resources. Advisor makes personalized recommendations based on resource configuration and telemetry, and provides you with guidance that most traditional monitoring platforms don't provide.


## Deep infrastructure monitoring (Log analytics, Management solution, Service Map, Network Monitoring)

When you're designing a monitoring strategy, it's important to include every component in the application chain, so you can correlate events across services and resources.

Services that support Azure Monitor can be easily configured to send their data to a Log Analytics workspace. Virtual machines (both in the cloud and on-premises) can have an agent installed to send data to Log Analytics. You can submit custom data to Log Analytics through the Log Analytics API.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_19.png?)

With this data in Log Analytics, you can query the raw data for troubleshooting, root cause identification, and auditing purposes. For several known services, like SQL Server and Windows Server Active Directory, there are readily-available management solutions that visualize monitoring data and uncover compliance with best practices.

Log Analytics allows you to create queries and interact with other systems based on those queries. The most common example is an alert. Maybe you want to receive an email when a system runs out of disk space, or a best practice on your SQL Servers is no longer being followed. Log Analytics can send alerts, kick off automation, and even hook into custom APIs for things like integration with IT service management (ITSM).


## Deep application monitoring (Application insights)

It's important to understand how core services and infrastructure are performing, but you can take your monitoring capabilities even further by looking deep into your applications to identify performance issues, usage trends, and the overall availability of services you develop and depend on. By using an application performance management tool, you can better detect and diagnose issues that occur within your web apps and services.

Azure Application Insights allows you to do exactly that. Application Insights provides telemetry collection, query, and visualization capabilities. Instrumenting this level of monitoring requires little to no code changes; you only have to install a small instrumentation package into your application. Application Insights is cross platform, supporting .NET, Node.js, or Java.

For instance, the response time for one of your applications might be complex to troubleshoot. For example: is the web server being overloaded? Is a specific SQL query not optimized? Is an API that you're calling performing slower than usual? Application performance monitoring solutions can help uncover the underlying issues that basic metric monitoring can't expose. The following screenshot shows a graphical display of an application’s performance details provided by Azure Application Insights.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_20.png?)


## Use automation to reduce effort and error

Managing the infrastructure for any type of workload involves configuration tasks. This configuration can be done manually, but manual steps do not scale well.


### Infrastructure as code

Infrastructure as code (IaC) is the management of infrastructure - such as networks, virtual machines, load balancers, and connection topology - in a descriptive model, using a versioning system that is similar to what is used for source code.

When you are creating an application, the same source code will generate the same binary every time it is compiled. In a similar manner, an IaC model generates the same environment every time it is applied. IaC is a key DevOps practice, and it is often used in conjunction with continuous delivery.

IaC evolved to solve the problem of environment drift. Without IaC, teams must maintain the settings of individual deployment environments. Over time, each environment becomes a snowflake that is increasingly unique, and cannot be reproduced automatically.

The administration and infrastructure maintenance of these snowflake environments involves manual processes that are hard to track and contribute to errors, and the resultant inconsistencies between these snowflake environments lead to issues during deployments.

When automating the deployment of services and infrastructure, there are two different approaches you can take: imperative and declarative.

- With an imperative approach, you explicitly state the commands that are executed to produce the outcome you are looking for.

- With a declarative approach, you specify what you want the outcome to be instead of specifying how you want it done.


#### Imperative automation

This is typically done programmatically through a scripting language or SDK. For Azure resources, we could use the Azure CLI or Azure PowerShell. Let's take a look at an example that uses the Azure CLI to create a storage account.

```
az group create \
    --name storage-resource-group \
    --location eastus

az storage account create \
    --name mystorageaccount \
    --resource-group storage-resource-group \
    --kind BlobStorage \
    --access-tier hot

```

With this approach, we're able to fully automate our infrastructure. We can provide areas for input and output, and can ensure that the same commands are executed every time. By automating our resources, we've taken the manual steps out of the process, making resource administration operationally more efficient.

However, there are some downsides to this approach. Scripts to create resources can quickly become complex as the architecture becomes more complex. Error handling and input validation may need to be added to ensure full execution. Commands may change, requiring ongoing maintenance of the scripts.


#### Declarative automation

With declarative automation, we're specifying what we want our result to be, leaving the details of how it's done to the system we're using. On Azure, declarative automation is done through the use of Azure Resource Manager (ARM) templates, which are **JSON-structured files** that specify what we want created. ARM templates have four sections: *parameters, variables, resources*, and *outputs*.

- Parameters handle input to be used within the template.
- Variables provide a way to store values for use throughout the template.
- Resources are the things that are being created.
- Outputs provide details to the user of what was created.

In the example below, we're telling Azure to create a storage account with the names and properties that we specify. The actual steps that are executed behind the scenes to create this storage account are left for Azure to decide.

```

{
    "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
    "contentVersion": "1.0.0.0",
    "parameters": {
        "name": {
            "type": "string"
        },
        "location": {
            "type": "string"
        },
        "accountType": {
            "type": "string",
            "defaultValue": "Standard_RAGRS"
        },
        "kind": {
            "type": "string"
        },
        "accessTier": {
            "type": "string"
        },
        "httpsTrafficOnlyEnabled": {
            "type": "bool",
            "defaultValue": true
        }
    },
    "variables": {
    },
    "resources": [
        {
            "apiVersion": "2018-02-01",
            "name": "[parameters('name')]",
            "location": "[parameters('location')]",
            "type": "Microsoft.Storage/storageAccounts",
            "sku": {
                "name": "[parameters('accountType')]"
            },
            "kind": "[parameters('kind')]",
            "properties": {
                "supportsHttpsTrafficOnly": "[parameters('httpsTrafficOnlyEnabled')]",
                "accessTier": "[parameters('accessTier')]",
                "encryption": {
                    "services": {
                        "blob": {
                            "enabled": true
                        },
                        "file": {
                            "enabled": true
                        }
                    },
                    "keySource": "Microsoft.Storage"
                }
            },
            "dependsOn": []
        }
    ],
    "outputs": {
        "storageAccountName": {
            "type": "string",
            "value": "[parameters('name')]"
        }
    }
}

```

You can use ARM templates to create and manipulate most services on Azure. You can store your templates in code repositories and inherit all the benefits of using a source control system, and you can share your templates across environments to ensure that the infrastructure you use for your development environment matches your production environment. ARM templates are a great way to automate deployments, and they help ensure consistency, eliminate deployment misconfigurations, and can increase operational speed.


### VM images vs. post-deployment configuration

For many virtual machine deployments, your job isn't done when a VM is simply up and running. In many situations, it's quite likely there's additional configuration that you need to take care of before the VM can actually serve its intended purpose.

There are two common strategies that you can use for the configuration work, which for all intents and purposes are considered to be part of the configuration process for the VM itself, and each of these strategies has its advantages and disadvantages.

- **Custom images** are generated by deploying a virtual machine, and then configuring or installing software on that running instance. When everything is configured correctly, the virtual machine can be shut down, and an image is created from the VM. This image can then be used as a base for deploying other new virtual machines. Working with custom images can speed up the overall time of your deployment, because as soon as the virtual machine is deployed and running, no additional configuration would be needed. *If deployment speed is an important factor, custom images are definitely worth exploring*.

- **Post-deployment** scripting typically leverages a basic base image, and then relies on scripting or a configuration management platform to perform the necessary configuration after the VM is deployed. The post-deployment scripting could be done by executing a script on the VM through the Azure Script Extension, or by leveraging a more robust solution such as *Azure Automation Desired State Configuration (DSC)*.

Each of these approaches has a few specific and some shared considerations to keep in mind.

- When using images, you'll need to ensure there's a process to handle image updates, security patches, and inventory management of the images themselves.

- With post-deployment scripting, build times can be extended since the VM can't be added to live workloads until the build is complete. This may not be a significant issue for standalone systems, but when using services that autoscale (such as virtual machine scale sets), this extended build time can impact how quickly you can scale.

- With both approaches, you'll want to ensure that you address configuration drift; as new configuration is rolled out, you'll need to ensure that existing systems are updated accordingly.


### Automation of operational tasks

Automating these tasks with Azure Automation reduces manual workloads, enables configuration and update management of compute resources, provides a framework for running any type of Azure task, and centralizes shared resources such as schedules, credentials, and certificates.

Examples of this automation might include:

- Periodically searching for orphaned disks
- Installing the latest security patches on VMs
- Searching for and shutting down virtual machines in off-hours
- Running daily reports and producing a dashboard to report to senior management

As an example, let's suppose that you want to reduce your compute costs by configuring one of your development virtual machines to run only during your organization's business hours. You can write a script to start the VM in the morning and shut it down in the evening, and you can configure Azure Automation to run the script at set times. The following illustration shows the role of Azure Automation in this process.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_21.png?)


### Automating development environments

At the other end of your cloud infrastructure pipeline are a collection of development machines, which are used by your developers to write the applications and services that are the core of your business. **You can use Azure DevTest Labs** to deploy VMs with all of the correct tools and repositories that your developers need. Developers working on multiple services can switch between development environments without having to provision a new VM themselves. These development environments can be shut down when they are not in use, and then restarted when they are required again.


## Testing strategies for your application

Testing is one of the fundamental components of DevOps and agile development in general.

A main tenet of a DevOps practice to achieve system reliability is the shift left principle.

Testing should occur on both application code and infrastructure code, and they should both be subject to the same quality controls. The environment where applications are running should be version-controlled, and deployed through the same mechanisms as application code. As a result, both application code and infrastructure code can be tested and validated using DevOps testing paradigms.

You can use your favorite testing tool to run your tests, including Azure Pipelines for automated testing and Azure Testing Plans for manual testing.

There are multiple stages at which tests can be performed in the life cycle of code, and each type of testing has several considerations that are important for you to understand.


### Automated Testing

Automating tests is the best way to make sure that they are executed.

#### Unit Testing

Unit tests are tests typically run by each new version of code that is committed into your version control system. Unit Tests should be extensive (should cover ideally 100% of the code), and quick (typically under 30 seconds, although this number is not a rule set in stone).

Unit testing could verify things like the syntax correctness of application code, Resource Manager templates or Terraform configurations, that the code is following best practices, or that they produce the expected results when provided certain inputs.

Unit tests should be applied both to application code and infrastructure code.


#### Smoke Testing

Smoke tests are more exhaustive than unit tests, but still not as much as integration tests. Smoke tests normally run in less than 15 minutes. While smoke tests do not verify the interoperability of your different components with each other, they verify that each component can be correctly built, and each component meets your criteria for expected functionality and performance.

Smoke tests usually involve building the application code; and if you're deploying infrastructure as part of your process, then possibly testing the deployment in a test environment.


#### Integration Testing

After making sure that your different application components operate correctly individually, integration testing determines whether your components can interact with each other as they should. Integration tests usually take longer than smoke testing; and as a consequence, they are sometimes executed less frequently. For example, running integration tests every night still offers a good compromise between the different types of automated testing; your integration testing will detect interoperability issues between application components no later than one day after they were introduced.


### Manual Testing

Manual testing is much more expensive than automated testing, and as a consequence it is used less frequently than automated testing


#### Acceptance Testing

There are many different ways of confirming that the application is doing what it should.

- Blue/Green deployments: when deploying a new application version, you can deploy it in parallel to the existing one. This way you can start redirecting your clients to the new version; if everything goes well, you will decommission the old version. If there is any problem with the new deployment, you can always redirect your clients back to the older deployment.

- Canary releases: you can expose new functionality of your application (ideally using feature flags) to a select group of users. If these users are satisfied with the new functionality, you can extend it to the rest of your user community. In this scenario we are talking about releasing functionality, and not necessarily about deploying a new version of the application.

- A/B testing: A/B testing is similar to canary release testing, but while canary releases focus on mitigating risk, A/B testing focuses on evaluating the effectiveness of two similar ways of achieving the same goal. For example, if you have two versions of the layout of a certain area of your application, you could send half of your users to one version and the other half your users to the other, and then you could use some metrics to see which layout works better for your application goals.


#### Stress tests

As other sections of this framework have explained, designing your application code and infrastructure for scalability is of paramount importance.

With this in mind, it is critical that you test whether your application and infrastructure code will both be able to adapt to changing load conditions.

During your stress tests, it is critical to that you monitor all the components of the system in order to identify whether there are any scale limitations.

Every component of the system that is not able to scale out can turn into a bottleneck (such as active/passive network components or databases). It is important for you to know the limits for each of your components so you can mitigate their impact into your application scale.

It is equally important to verify that after the stress test is concluded, your infrastructure scales back down to its normal condition in order to keep your costs under control.


#### Fault injection

Your application should be resilient to infrastructure failures, and introducing faults in the underlying infrastructure and observing how your application behaves is fundamental for increasing the trust in your redundancy mechanisms.

For example: ungracefully shutting down infrastructure components, degrading the performance of certain elements such as network equipment, or purposely introducing faults in the environment are ways of verifying that your application is going to continue to behave or react as expected, should these situations ever occur in real life.

Most companies use a controlled way of injecting faults into the system; although if your are confident with your application resiliency, you could use automated frameworks

#### Security tests

Another critical component of your test strategy should be routine testing of your application for security vulnerabilities. You should regularly perform security tests against your application to identify any application vulnerabilities that are introduced through code defects or through software dependencies.

These tests can include automated security scans to test against common vulnerabilities, such as cross-site scripting or SQL injection. Your security tests can also include red team exercises, where security teams attempt to compromise your application.

***

# Microsoft Azure Well-Architected Framework - Performance efficiency


## Use scaling up and scaling out in your architecture

### What is scaling?

When we look at ways to increase or decrease the compute capacity and relative costs for your applications, it's important to define two key concepts: *scaling* and *resources*.

- **Scaling** is the process of managing your resources to help your application meet a set of performance requirements. When you have too many resources serving your users, you won't be using those resources efficiently, and you'll be wasting money. When you have too few resources available, the performance of your application can be adversely affected. Your goal is to meet your defined performance requirements while optimizing for cost.
- **Resources** can refer to anything you need to manage and run your applications. Memory and CPUs for virtual machines are the most obvious resources. But some Azure services might require you to consider bandwidth or abstractions, like Request Units (RUs) for Azure Cosmos DB.


### What is scaling up or down?


When you use a single instance of a service, such as a virtual machine, you might need to scale the number of resources that are available to your instance.

- **Scaling up** is the process where you increase the capacity of a given instance. For example, to increase your processing capacity, you might increase a virtual machine from 1 vCPU and 3.5 GB of RAM to 2 vCPUs and 7 GB of RAM.
- **Scaling down** is the process where you decrease the capacity of a given instance. For example, you might decrease a virtual machine's capacity from 2 vCPUs and 7 GB of RAM to 1 vCPU and 3.5 GB of RAM. In this way, you reduce capacity and cost.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_22.png?)


Let's look at what scaling up or down means in the context of Azure resources:

- In **Azure virtual machines**, you scale based on a virtual machine size. Each VM size has a certain amount of vCPUs, RAM, and local storage associated with it. For example, you could scale up from a Standard_DS1_v2 virtual machine (1 vCPU and 3.5 GB of RAM) to a Standard_DS2_v2 virtual machine (2 vCPUs and 7 GB of RAM).

- **Azure SQL Database** is a platform as a service (PaaS) implementation of Microsoft SQL Server. You can scale up a database based on the number of database transaction units (DTUs) or vCPUs. DTUs are an abstraction of underlying resources and are a blend of CPU, IO, and memory. For example, you could scale your database in Azure SQL Database from a size of P2 with 250 DTUs up to a P4 with 500 DTUs to give the database more throughput and capacity.

- **Azure App Service** is a PaaS website-hosting service on Azure. Websites run on a virtual server farm, which is also known as an App Service plan. You can scale the App Service plan up or down between tiers. You also have capacity options within those tiers. For example, an S1 App Service plan has 1 vCPU and 1.75 GB of RAM per instance. You could scale up to an S2 App Service plan, which has 2 vCPUs and 3 GB of RAM per instance.


### What is scaling out or in?

You now know that scaling up and down adjusts the amount of resources a single instance has available. Scaling out and in adjusts the total number of instances.

- **Scaling out** is the process of adding more instances to support the load of your solution. For example, if your website front ends were hosted on virtual machines, you could increase the number of virtual machines if the level of load increased.
- **Scaling in** is the process of removing instances that are no longer needed to support the load of your solution. If your website front ends have low usage, you might want to lower the number of instances to save cost.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_23.png?)

Here are some examples of what scaling out or in means in the context of Azure resources:

- For the infrastructure layer, you would likely use virtual machine scale sets to automate the addition and removal of extra instances.
  - Virtual machine scale sets let you create and manage a group of identical, load-balanced VMs.
  - The number of VM instances can automatically increase or decrease in response to demand or a defined schedule.
- In an Azure SQL Database implementation, you could share the load across database instances by sharding. Sharding is a technique to distribute large amounts of identically structured data across a number of independent databases.
- In Azure App Service, the App Service plan is the virtual web server farm that hosts your application. Scaling out in this way means that you're increasing the number of virtual machines in the farm. As with virtual machine scale sets, the number of instances can be automatically raised or lowered in response to certain metrics or a schedule.

Scaling out is easily performed via the Azure portal, command-line tools, or Azure Resource Manager templates. In most cases, it's seamless to the user.


#### Autoscale

You can configure some of these services to use a feature called autoscale. With autoscale, you no longer have to worry about scaling services manually. Instead, you can set a minimum and maximum threshold of instances.

An example is weekdays between 5:00 PM and 7:00 PM. The following illustration shows how the autoscale feature manages instances to handle the load.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_24.png?)

#### Considerations when you scale in and out

When you scale out, the startup time of your application can impact how quickly your application can scale. If your web app takes two minutes to start up and become available for users, that means each of your instances will take two minutes until they're available to your users. You need to consider this startup time when you determine how fast you want to scale.

You also need to think about how your application handles state. When the application scales in, any state that was stored on the instance that's removed from your environment will be lost. 

If a user connects to an instance that doesn't have its state, your application might force the user to sign in or reselect their data. The result is a poor user experience. 

A common pattern is to externalize your state to another service, like Azure Cache for Redis or SQL Database, which makes your web servers stateless. Now that your web front ends are stateless, you don't need to worry about which individual instances are available. They're all doing the same job and are deployed in the same way.


### Throttling

We've established that the load on an application varies over time. This variation might be because of the number of active or concurrent users and the activities that are being performed. You can use autoscaling to add capacity. But you can also use a throttling mechanism to limit the number of requests from a source. You can safeguard performance limits by putting known limits into place at the application level. In this way, you prevent the application from breaking. 

*Throttling is most frequently used in applications that expose API endpoints.*

After the application has identified that it would breach a limit, throttling could begin and ensure the overall system SLA isn't breached. For example, if you exposed an API for customers to get data, you could limit the number of requests to 100 per minute. If any single customer exceeded this limit, you could respond with an HTTP 429 status code and include the wait time before another request can successfully be submitted.


### Serverless

You configure your serverless apps to respond to events. An event can be a REST endpoint, a timer, or a message received from another Azure service. The serverless app runs only when it's triggered by an event.

When you work with serverless apps, infrastructure isn't your responsibility. Scaling and performance are handled automatically. You're only billed for the resources you use. There's no need to reserve capacity. **Azure Functions, Azure Container Instances, and Azure Logic Apps** are examples of serverless computing available on Azure.


### Containers

A container is a method of running applications in a virtualized environment. A virtual machine is virtualized at the hardware level, where a hypervisor makes it possible to run multiple virtualized operating systems on a single physical server. 

Containers take the virtualization up a level. The virtualization is done at the OS level, which makes it possible to run multiple identical application instances within the same OS.

Containers are lightweight and well suited to scale-out scenarios. They're designed to be created, scaled out, and stopped dynamically as your environment and demands change. Another benefit of using containers is the ability to run multiple isolated applications on each virtual machine. Because containers are secured and isolated at a kernel level, you don't necessarily need to separate VMs for separate workloads.

Although you can run containers on virtual machines, there are a couple of Azure services that ease the management and scaling of containers:

- **Azure Kubernetes Service (AKS)**

    With Azure Kubernetes Service, you can set up virtual machines to act as your nodes. Azure hosts the Kubernetes management plane. You're charged only for the running worker nodes that host your containers.

    To increase the number of your worker nodes in Azure, you can use the Azure CLI to increase that number manually. At the time of this writing, a preview of Cluster Autoscaler on AKS is available. It enables autoscaling of your worker nodes. On your Kubernetes cluster, you can use the Horizontal Pod Autoscaler to scale out the number of instances of the container to be deployed.

 - **Azure Container Instances**

    Azure Container Instances is a serverless approach that lets you create and execute containers on demand. You're charged only for the execution time per second.

    You can use Virtual Kubelet to connect Azure Container Instances into your Kubernetes environment, which includes AKS. With Virtual Kubelet, when your Kubernetes cluster demands additional container instances, those demands can be met from Container Instances. Because Container Instances is serverless, there's no need to have reserved capacity. You can take advantage of the control and flexibility of Kubernetes scaling with the per-second-billing of serverless. At the time of this writing, the Virtual Kubelet is described as experimental software and shouldn't be used in production scenarios.


## Optimize Network Performance

Network performance can have a dramatic impact on a user's experience


### The importance of network latency

Latency is a measure of delay. Network latency is the time that it takes for data to travel between a source to a destination across a network.

The time that it takes for data to travel from the source to a destination and for the destination to respond is commonly known as a round-trip delay.

All Azure regions are interconnected by a high-speed fiber backbone, the speed of light is still a physical limitation. Calls between services in different physical locations will still have network latency directly correlated to the distance between them.

In addition, depending on the communication needs of an application, more round trips might be required. Each round trip comes with a latency tax, and each round trip adds to the overall latency. The following illustration shows how the latency perceived by the user is the combination of the round trips required to service the request.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_25.png?)


### Latency between Azure resources

Imagine that you work for a healthcare organization that's pilot testing a new patient booking system. This system runs on several web servers and a database. All of the resources are located in the West Europe Azure region. The scope of your pilot test is available only for users in Western Europe. This architecture minimizes your network latency, because all of your resources are colocated inside a single Azure region

Suppose that your pilot testing of the booking system was successful. As a result, the scope of your pilot test has expanded to include users in Australia. When the users in Australia view your website, they'll incur the additional round-trip time that's necessary to access all of the resources that are located in West Europe. Their experience will be diminished because of the additional network latency.

To address your network latency issues, your IT team decides to host another front-end instance in the Australia East region. This design helps reduce the time for your web servers to return content to users in Australia. But their experience is still diminished because there's significant latency for data that's being transferred between the front-end web servers in Australia East and the database in West Europe.

There are a few ways you could reduce the remaining latency:

- Create a read-replica of the database in Australia East. A read replica allows reads to perform well, but writes still incur latency. Azure SQL Database geo-replication allows for read-replicas.
- Sync your data between regions with Azure SQL Data Sync.
- Use a globally distributed database such as Azure Cosmos DB. This database allows both reads and writes to occur regardless of location. But it might require changes to the way your application stores and references data.
- Use caching technology, such as Azure Cache for Redis, to minimize high-latency calls to remote databases for frequently accessed data.


### Latency between users and Azure resources

You want to optimize delivery of the front-end user interface to your users. Let's look at some ways to improve the network performance between your users and your application.

#### Use a DNS load balancer for endpoint path optimization

In our example scenario, your IT team created an additional web front-end node in Australia East. But users have to explicitly specify which front-end endpoint they want to use. As the designer of a solution, you want to make the experience as smooth as possible for users.

**Azure Traffic Manager** could help. Traffic Manager is a DNS-based load balancer that you can use to distribute traffic within and across Azure regions.

Rather than having the user browse to a specific instance of your web front end, Traffic Manager can route users based on a set of characteristics:

- **Priority**: You specify an ordered list of front-end instances. If the one with the highest priority is unavailable, Traffic Manager routes the user to the next available instance.
- **Weighted**: You set a weight against each front-end instance. Traffic Manager then distributes traffic according to those defined ratios.
- **Performance**: Traffic Manager routes users to the closest front-end instance based on network latency.
- **Geographic**: You set up geographical regions for front-end deployments and route your users based on data sovereignty mandates or localization of content.

Traffic Manager profiles can also be nested. For example, you could initially route your users across different geographies (such as Europe and Australia) by using geographic routing. Then you can route them to local front-end deployments by using the performance routing method.

It's important to note that this load balancing is only handled via DNS. No inline load balancing or caching is happening here. Traffic Manager simply returns the DNS name of the closest front end to the user.


#### Use a CDN to cache content close to users

Your website likely uses some form of static content, either whole pages or assets such as images and videos. This static content can be delivered to users faster by using a content delivery network (CDN), such as **Azure Content Delivery Network**.

With content deployed to Azure Content Delivery Network, those items are copied to multiple servers around the globe.

This approach puts content closer to the destination, which reduces latency and improves the user experience. The following illustration shows how using Azure Content Delivery Network puts content closer to the destination, which reduces latency and improves the user experience.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_26.png?)


Content delivery networks can also be used to host cached dynamic content. Extra consideration is required though, because cached content might be out of date compared with the source. Context expiration can be controlled by setting a *time to live (TTL)*. If the TTL is too high, out-of-date content might be displayed and the cache would need to be purged.

One way to handle cached content is with a feature called *dynamic site acceleration*, which can increase performance of webpages with dynamic content. Dynamic site acceleration can also provide a low-latency path to additional services in your solution. An example is an *API endpoint*.


#### Use ExpressRoute for connectivity from on-premises to Azure

Optimizing network connectivity from your on-premises environment to Azure is also important. For users who connect to applications, whether they're hosted on virtual machines or on platform as a service (PaaS) offerings like Azure App Service, you'll want to ensure they have the best connection to your applications.

You might want a private connection to your Azure resources. Site-to-site VPN over the internet is also an option. VPN overhead and internet variability can have a noticeable impact on network latency for high-throughput architectures.

**Azure ExpressRoute** can help. ExpressRoute is a private, dedicated connection between your network and Azure. It gives you guaranteed performance and ensures that your users have the best path to all of your Azure resources. The following illustration shows how an ExpressRoute circuit provides connectivity between on-premises applications and Azure resources.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_27.png?)


## Optimize storage performance

It's important to include storage performance considerations in your architecture. Just like network latency, poor performance at the storage layer can affect your user experience.

### Optimize virtual machine storage performance

Different applications have different storage requirements. Your application might be sensitive to latency of disk reads and writes. Or, it might require the ability to handle a large number of input/output operations per second (IOPS) or greater overall disk throughput.

When you build an infrastructure as a service (IaaS) workload, which type of disk should you use? There are four options:

- **Local SSD storage**: Each virtual machine has a temporary disk that's backed by local SSD storage. The size of this disk varies depending on the size of the virtual machine. Because this SSD is local to the virtual machine, the performance is high. But data could be lost during a maintenance event or a redeployment of the VM. This disk is only suitable for temporary storage of data that you don't need permanently. For example, this disk is great for the VM's page or swap file, and for things like tempdb in Azure SQL Server. There's no charge for this storage. It's included in the cost of the VM.
- **Standard storage HDD**: This type of storage is spindle disk storage. It might fit well where your application isn't bound by inconsistent latency or lower levels of throughput. A dev/test workload where guaranteed performance isn't required is a great use case for this disk type.
- **Standard storage SSD**: This SSD-backed storage has the low latency of an SSD, but with lower levels of throughput. A non-production web server is a good use case for this disk type.
- **Premium storage SSD**: This SSD-backed storage is well suited for those workloads that are going into production and require the greatest reliability, demand consistent low latency, or need high levels of throughput and IOPS. Because these disks have greater performance and reliability capabilities, they're recommended for all production workloads.

Premium storage can attach only to specific VM sizes. Premium storage-capable sizes are designated with an "s" in the name. 
Examples are D2s_v3 or Standard_F2s_v2. Any virtual machine type (with or without an "s" in the name) can attach standard storage HDD or SSD drives.

Disks can be striped by using a striping technology like Storage Spaces on Windows or mdadm on Linux. Striping increases the throughput and IOPS by spreading disk activity across multiple disks. You can use disk striping to push the limits of performance for disks. Striping is often seen in high-performance database systems and other systems with intensive storage requirements.


### Optimize storage performance for your application

#### Caching

A common approach to improve application performance is to integrate a caching layer between your application and your data store.

A cache typically stores data in memory and allows for fast retrieval. This data can be frequently accessed data, data that you specify from a database, or temporary data such as user state

You have control over the type of data stored, how often it refreshes, and when it expires. By colocating this cache in the same region as your application and database, you reduce the overall latency between the two. Pulling data out of the cache is almost always faster than retrieving the same data from a database.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_28.png?)

**Azure Cache** for Redis is a caching service on Azure that stores data in memory. It's based on the open-source **Redis cache** and is a fully managed service offering by Microsoft. You select the performance tier that you require, and then you configure your application to use the service.

#### Polyglot persistence

Polyglot persistence is the use of different data storage technologies to handle your storage requirements.

Consider the following e-commerce example. Suppose that you store application assets in a blob store, product reviews and recommendations in a NoSQL store, and user profile or account data in a SQL database. The following illustration shows how an application might use multiple data storage techniques to store different types of data.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_29.png?)

It's important to know that different data stores are designed for certain use cases or might be more accessible because of cost. As an example, storing blobs in a SQL database might be costly and slower to access than directly from a blob store.

Maintaining data consistency across distributed data stores can be a significant challenge. 

**Eventual consistency** means that replica data stores eventually converge if there are no further writes. If a write is made to one of the data stores, reads from another data store might provide slightly out-of-date data. Eventual consistency enables higher scale because there's a low latency for reads and writes, instead of waiting to check if information is consistent across all stores.


## Identify performance bottlenecks in your application

### Performance requirements

*Nonfunctional requirements* help you find that point. These particular requirements don't tell you what your app must do. Instead, they tell you what quality levels it must meet. For example, you can define nonfunctional requirements to discover:

- How fast a transaction must return under a given load.
- How many simultaneous connections your application needs to support before it begins to return errors.
- If there's server failure, what's the maximum amount of time your application is allowed to be down before a backup is online.

### Performance monitoring options in Azure

Monitoring is the act of collecting and analyzing data to determine the performance, health, and availability of your business application and associated resources.

You want to be kept informed that your applications are running smoothly. Proactive notifications can be used to inform about critical issues that arise. There are many layers of monitoring to consider. Let's focus on the infrastructure layer and the application layer.

#### Azure Monitor

Azure Monitor provides a single management point for infrastructure-level logs and monitoring for most of your Azure services.

Azure Monitor maximizes the availability and performance of your applications by delivering a comprehensive solution for collecting, analyzing, and acting on telemetry from your cloud and on-premises environments.

The following diagram depicts a high-level view of Azure Monitor. At the center of the diagram are the data stores for metrics and logs. These are the two fundamental types of data that Azure Monitor uses. On the left side are the sources of monitoring data that populate these data stores. On the right side are the different functions that Azure Monitor performs with this collected data, such as analysis, alerting, and streaming to external systems.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_30.png?)

Azure Monitor can collect data from a variety of sources. You can think of monitoring data for your applications as occurring in tiers that range from your application to any OS and the services it relies on to the platform itself.

Azure Monitor collects data from each of the following tiers:

- **Application monitoring data**: Data about the performance and functionality of the code you've written, regardless of its platform.
- **Guest OS monitoring data**: Data about the OS on which your application is running. This OS might be in Azure, another cloud, or on-premises.
- **Azure resource monitoring data**: Data about the operation of an Azure resource.
- **Azure subscription monitoring data**: Data about the operation and management of an Azure subscription, and data about the health and operation of Azure itself.
- **Azure tenant monitoring data**: Data about the operation of tenant-level Azure services, such as Azure Active Directory (Azure AD).

As soon as you create an Azure subscription and start adding resources, such as VMs and web apps, Azure Monitor starts collecting data.

- Activity logs record when resources are created or modified.
- Metrics tell you how the resource is performing and the resources that it's consuming.
- You can also extend the data you collect.
- You can enable diagnostics in your apps and add agents to collect telemetry data from Linux and Windows or Application Insights.

Azure Monitor is the place to start for all your resource metric insights gathered in near real time. Many Azure resources start outputting metrics automatically after they're deployed. For example, web apps built with the Web Apps feature of Azure App Service output compute and application request metrics. Metrics from Application Insights are also collated here in addition to VM host diagnostic metrics. VM guest diagnostic metrics also appear after you opt in.

#### Log Analytics

Centralized logging can help you uncover hidden issues that might be difficult to track down. With Log Analytics, you can query and aggregate data across logs.

This cross-source correlation can help you identify issues or performance problems that might not be evident when you look at logs or metrics individually. The following illustration shows how Log Analytics acts as a central hub for monitoring data. Log Analytics receives monitoring data from your Azure resources and makes it available to consumers for analysis or visualization.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_31.png?)

You can collate a wide range of data sources, security logs, Azure activity logs, and server, network, and application logs. You can also push on-premises System Center Operations Manager data to Log Analytics in hybrid deployment scenarios. Then Azure SQL Database can send diagnostic information directly into Log Analytics for detailed performance monitoring.

*Centralized logging can be highly beneficial for troubleshooting all types of scenarios. You can use it to troubleshoot performance issues. Centralized logging is a key part of a good monitoring strategy for any architecture.*


### Application performance management

Deep application issues are often tricky to track down. This type of scenario is when it can be beneficial to integrate telemetry into your application by using an application performance management (APM) solution

An APM solution helps you to track down low-level application performance and behavior. Telemetry can include individual page request times, exceptions within your application, and even custom metrics to track business logic. This telemetry can provide a wealth of insight into what's going on within your application.

**Application Insights** is an Azure service that provides this deep application performance management. You install a small instrumentation package in your application and then set up an Application Insights resource in the Azure portal.

You can use Application Insights to consume telemetry from the host environments, such as ```performance counters, Azure diagnostics,``` and ```Docker logs```.

You can also set up web tests that periodically send synthetic requests to your web service. You could even configure your application to send custom events and metrics that you write yourself in the client or server code. For example, you can track application-specific events such as items sold or games won.

Application Insights stores its data in a common repository, and metrics are shared with Azure Monitor. Application Insights can also take advantage of shared functionality such as alerts, dashboards, and deep analysis with the Log Analytics query language.

A common pattern used to determine the availability of a web application is the health endpoint monitoring pattern. This pattern is used to monitor web applications and their associated back-end services to ensure that they're available and performing correctly. The pattern is implemented by querying a particular URI. The endpoint checks on the status of many components. Even the back-end services that the app depends on are checked instead of only the availability of the front end itself. The health endpoint monitoring pattern acts as a service-level health check that returns an indication of the overall health of the service.

***

# Microsoft Azure Well-Architected Framework - Reliability


## Build a highly available architecture

High availability (HA) ensures your architecture can handle failures.


### What is high availability?

A highly available service is a service that absorbs fluctuations in availability, load, and temporary failures in dependent services and hardware. The application remains online and available (or maintains the appearance of it) while performing acceptably. This availability is often defined by business requirements, service-level objectives, or service-level agreements.

### Evaluate high availability for your architecture

There are three steps to evaluate an application for high availability:

- Determine the service-level agreement of your application
- Evaluate the HA capabilities of the application
- Evaluate the HA capabilities of dependent applications

Let's explore these steps in detail.

#### Determine the service-level agreement of your application

*A service-level agreement (SLA)* is an agreement between a service provider and a service consumer in which the service provider commits to a standard of service based on measurable metrics and defined responsibilities.

*Service-level objectives (SLO)* are the values of target metrics that are used to measure performance, reliability, or availability. These could be metrics defining the performance of request processing in milliseconds, the availability of services in minutes per month, or the number of requests processed per hour. By evaluating the metrics exposed by your application and understanding what customers use as a measure of quality, you can define the acceptable and unacceptable ranges for these SLOs

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_32.png?)

Here are some other considerations when defining an SLA:

- To achieve four 9's (99.99%), you probably can't rely on manual intervention to recover from failures. The application must be self-diagnosing and self-healing.
- Beyond four 9's, it is challenging to detect outages quickly enough to meet the SLA.
- Think about the time window that your SLA is measured against. The smaller the window, the tighter the tolerances. It probably doesn't make sense to define your SLA in terms of hourly or daily uptime.


#### Evaluate the HA capabilities of the application

To evaluate the HA capabilities of your application, perform a failure analysis. Focus on single points of failure and critical components that would have a large impact on the application if they were unreachable, misconfigured, or started behaving unexpectedly

For areas that do have redundancy, determine whether the application is capable of detecting error conditions and self-healing.

You'll need to carefully evaluate all components of your application, including the pieces designed to provide HA functionality, such as load balancers. Single points of failure will either need to be modified to have HA capabilities integrated, or will need to be replaced with services that can provide HA capabilities.


#### Evaluate the HA capabilities of dependent applications

You'll need to understand not only your application's SLA requirements to your consumer, but also the provided SLAs of any resource that your application may depend on. If you are committing an uptime to your customers of 99.9%, but a service your application depends on only has an uptime commitment of 99%, this could put you at risk of not meeting your SLA to your customers. If a dependent service is unable to provide a sufficient SLA, you may need to modify your own SLA, replace the dependency with an alternative, or find ways to meet your SLA while the dependency is unavailable.


### Azure's highly available platform

The Azure cloud platform has been designed to provide high availability throughout all its services. Like any system, applications may be affected by both hardware and software platform events.

There are several core concepts when considering HA for your architecture on Azure:

- Availability sets
- Availability zones
- Load balancing
- Platform as a service (PaaS) HA capabilities


#### Availability sets

Availability sets are a way for you to inform Azure that VMs that belong to the same application workload should be distributed to prevent simultaneous impact from hardware failure and scheduled maintenance. Availability sets are made up of update domains and fault domains.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_33.png?)

**Update domains** ensure that a subset of your application's servers always remain running when the virtual machine hosts in an Azure datacenter require downtime for maintenance. Most updates can be performed with no impact to the VMs running on them, but there are times when this isn't possible. To ensure that updates don't happen to a whole datacenter at once, the Azure datacenter is logically sectioned into update domains (UD).

When a maintenance event, such as a performance update and critical security patch that needs to be applied to the host, the update is sequenced through update domains. The use of sequencing updates using update domains ensures that the whole datacenter isn't unavailable during platform updates and patching.

While update domains represent a logical section of the datacenter, **fault domains (FD)** represent physical sections of the datacenter and ensure rack diversity of servers in an availability set. Fault domains align to the physical separation of shared hardware in the datacenter. This includes power, cooling, and network hardware that supports the physical servers located in server racks. In the event the hardware that supports a server rack has become unavailable, only that rack of servers would be affected by the outage. By placing your VMs in an availability set, your VMs will be automatically spread across multiple FDs so that in the event of a hardware failure only part of your VMs will be impacted.


#### Availability zones

Availability zones are independent physical datacenter locations within a region that include their own power, cooling, and networking. By taking availability zones into account when deploying resources, you can protect workloads from datacenter outages while retaining presence in a particular region. Services like virtual machines are zonal services and allow you to deploy them to specific zones within a region. Other services are zone-redundant services and will replicate across the availability zones in the specific Azure region. Both types ensure that within an Azure region there are no single points of failure.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_34.png?)

Supported regions contain a minimum of three availability zones. When creating zonal service resources in those regions, you'll have the ability to select the zone in which the resource should be created.

Availability zones are supported when using virtual machines, as well as several PaaS services.

Availability zones are mutually exclusive with availability sets. When using availability zones, you no longer need to define an availability set for your systems. You'll have diversity at the data center level, and updates will never be performed to multiple availability zones at the same time.


#### Load balancing

Load balancers manage how network traffic is distributed across an application. For applications that don't have service discovery built in, load balancing is required for both availability sets and availability zones.

Azure possesses three load balancing technology services that are distinct in their abilities to route network traffic:

- **Azure Traffic Manager** provides global DNS load balancing. You would consider using Traffic Manager to provide load balancing of DNS endpoints within or across Azure regions. Traffic manager will distribute requests to available endpoints, and use endpoint monitoring to detect and remove failed endpoints from load.

- **Azure Application Gateway** provides Layer 7 load-balancing capabilities, such as round-robin distribution of incoming traffic, cookie-based session affinity, URL path-based routing, and the ability to host multiple websites behind a single application gateway. Application Gateway by default monitors the health of all resources in its back-end pool and automatically removes any resource considered unhealthy from the pool. Application Gateway continues to monitor the unhealthy instances and adds them back to the healthy back-end pool once they become available and respond to health probes.

- **Azure Load Balancer** is a layer 4 load balancer. You can configure public and internal load-balanced endpoints and define rules to map inbound connections to back-end pool destinations by using TCP and HTTP health-probing options to manage service availability.

One or a combination of all three Azure load-balancing technologies can ensure you have the necessary options available to architect a highly available solution to route network traffic through your application.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_35.png?)


#### PaaS HA capabilities

PaaS services come with high availability built in. Services such as Azure SQL Database, Azure App Service, and Azure Service Bus include high availability features and ensure that failures of an individual component of the service will be seamless to your application. Using PaaS services is one of the best ways to ensure that your architecture is highly available.


## Develop a disaster recovery strategy

You should know what your goals and expectations are for recovering, what are the costs and limitations of your plan, and how to execute on it.


### What is disaster recovery?

Disaster recovery is about recovering from high-impact events that result in downtime and data loss. A disaster is a single, major event with an impact much larger and long-lasting than the application can mitigate through the high-availability portion of its design.

A failed deployment or upgrade can leave an app in an unrecognizable state. Malicious hackers can encrypt or delete data and inflict other kinds of damage that take an app offline or eliminate some of its functionality.

Regardless of its cause, the best remedy for a disaster once it has occurred is a well-defined, tested disaster recovery plan and an application that actively supports disaster recovery efforts through its design.


### How to create a disaster recovery plan

A disaster recovery plan is a single document that details the procedures that are required to recover from data loss and downtime caused by a disaster, and identifies who's in charge of directing those procedures.

Operators should be able to use the plan as a manual to restore application connectivity and recover data after a disaster occurs.

Creating a disaster recovery plan requires expert knowledge of the application's workflows, data, infrastructure, and dependencies.


#### Risk assessment and process inventory

The first step in creating a disaster recovery plan is performing a risk analysis that examines the impact of different kinds of disasters on the application.

The exact nature of a disaster isn't as important to the risk analysis as its potential impact through data loss and application downtime.

Explore various kinds of hypothetical disasters and try to be specific when thinking about their effects.

The risk assessment needs to consider every process that can't afford unlimited downtime, and every category of data that can't afford unlimited loss. When a disaster that affects multiple application components occurs, it's critical that the plan owners can use the plan to take a complete inventory of what needs attention and how to prioritize each item.

Some apps may only constitute a single process or classification of data. This is still important to note, as the application will likely be one component of a larger disaster recovery plan that includes multiple applications with the organization.


#### Recovery objectives

A complete plan needs to specify two critical business requirements for each process implemented by the application:

- **Recovery Point Objective (RPO)**: The maximum duration of acceptable data loss. RPO is measured in units of time, not volume: "30 minutes of data", "four hours of data", and so on. RPO is about limiting and recovering from data loss, not data theft.

- **Recovery Time Objective (RTO)**: The maximum duration of acceptable downtime, where "downtime" needs to be defined by your specification. For example, if the acceptable downtime duration is eight hours in the event of a disaster, then your RTO is eight hours.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_36.png?)

Each major process or workload that's implemented by an app should have separate RPO and RTO values.

The process of specifying an RPO and RTO is effectively the creation of disaster recovery requirements for your application. It requires establishing the priority of each workload and category of data and performing a cost-benefit analysis.

The analysis includes concerns, such as implementation and maintenance cost, operational expense, process overhead, performance impact, and the impact of downtime and lost data.


#### Detailing recovery steps

The final plan should go into detail about exactly what steps should be taken to restore lost data and application connectivity. Steps often include information about:

- **Backups**: How often they're created, where they're located, and how to restore data from them.

- **Data replicas**: The number and locations of replicas, the nature and consistency characteristics of the replicated data, and how to switch over to a different replica.

- **Deployments**: How deployments are executed, how rollbacks occur, and failure scenarios for deployments.

- **Infrastructure**: On-premises and cloud resources, network infrastructure, and hardware inventory.

- **Dependencies**: External services that are used by the application, including SLAs and contact information.

- **Configuration and notification**: Flags or options that can be set to gracefully degrade the application, and services that are used to notify users of application impact.


### Designing for disaster recovery

Disaster recovery is not an automatic feature. It must be designed, built, and tested. An app that needs to support a solid disaster recovery strategy must be built from the ground up with disaster recovery in mind.

Designing for disaster recovery has two main concerns:

- **Data recovery**: Using backups and replication to restore lost data.

- **Process recovery**: Recovering services and deploying code to recover from outages.


#### Data recovery and replication

Replication duplicates stored data between multiple data store replicas. Unlike backup, which creates long-lived, read-only snapshots of data for use in recovery, replication creates real-time or near-real-time copies of live data. 

Replication is used to mitigate a failed or unreachable data store by executing a failover: changing application configuration to route data requests to a working replica. Failover is often automated, triggered by error detection built into a data storage product, or detection that you implement through your monitoring solution.

Replication is not something you implement from scratch. Most fully featured database systems and other data storage products and services include some kind of replication as a tightly integrated feature due to its functional and performance requirements

Different Azure services support various levels and concepts of replication. For example:

- **Azure Storage replication** capabilities depend on the type of replication that is selected for the storage account. This replication can be local (within a datacenter), zonal (between data centers within a region), or regional (between regions). Neither your application nor your operators interact with it directly. Failovers are automatic and transparent, and you simply need to select a replication level that balances cost and risk.

- **Azure SQL Database replication** is automatic at a small scale, but recovery from a full Azure datacenter or regional outage requires geo-replication. *Setting up geo-replication is manual*, but it's a first-class feature of the service and well supported by documentation.

- **Azure Cosmos DB** is a globally distributed database system, and replication is central to its implementation. With Azure Cosmos DB you configure options related to regions associated with your database, data partitioning, and data consistency.

Many different replication designs exist that place different priorities on data consistency, performance, and cost. 

- *Active* replication requires updates to take place on multiple replicas simultaneously, guaranteeing consistency at the cost of throughput

- *Passive* replication performs synchronization in the background, removing replication as a constraint on application performance, but increasing RPO.

- *Active-active or multi-master replication* enables multiple replicas to be used simultaneously, enabling load balancing at the cost of complicating data consistency, while active-passive replication reserves replicas for live use only during failover.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_37.png?)

    Important

    Neither replication nor backup are complete disaster recovery solutions on their own. Data recovery is only one component of disaster recovery, and replication will not fully satisfy many kinds of disaster recovery scenarios. For example, in a data corruption scenario, the nature of the corruption may allow it to spread from the primary data store to the replicas, rendering all the replicas useless and requiring a backup for recovery.

#### Process recovery

After a disaster, business data isn't the only asset that needs recovering. Disaster scenarios will also commonly result in downtime, whether it's due to network connectivity problems, datacenter outages, or damaged VM instances or software deployments. The design of your application needs to enable you to restore it to a working state.

Depending on the design of your application, there are a few different strategies and Azure services and features that you can take advantage of to improve your app's support for process recovery after a disaster.


#### Azure Site Recovery

Azure Site Recovery is a service that's dedicated to managing process recovery for workloads running on VMs deployed to Azure, VMs running on physical servers, and workloads running directly on physical servers. Site Recovery replicates workloads to alternate locations and helps you to failover when an outage occurs and supports testing of a disaster recovery plan.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_38.png?)

Site Recovery supports replicating whole VMs and physical server images as well as individual *workloads*, where a workload may be an individual application or an entire VM or operating system with its applications.

Any application workload can be replicated, but Site Recovery has first-class integrated support for many Microsoft server applications, such as SQL Server and SharePoint, as well as a handful of third-party applications like SAP.

Any app that runs on VMs or physical servers should at least investigate the use of Azure Site Recovery. It's a great way to discover and explore scenarios and possibilities for process recovery.


#### Service-specific features

For apps that run on Azure PaaS offerings like App Service, most such services offer features and guidance for supporting disaster recovery. For certain scenarios, you can use service-specific features to support fast recovery. For example, Azure SQL Server supports geo-replication for quickly restoring service in another region. Azure App Service has a Backup and Restore feature, and the documentation includes guidance for using Azure Traffic Manager to support routing traffic to a secondary region.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_39.png?)


### Testing a disaster recovery plan

Disaster recovery planning doesn't end once you have a completed plan in hand. Testing the plan is a crucial aspect of disaster recovery, to ensure that the directions and explanations are clear and up-to-date.


## Protect your data with backup and restore

Backup is the final and most powerful line of defense against permanent data loss.

### Establish backup and restoration requirements

To establish backup requirements for your app, group your application's data based on the following requirements:

- How much of this type of data can afford to be lost, measured in duration
- The maximum amount of time a restore of this type of data should require
- Backup retention requirements: how long and at what frequency do backups need to remain available

Backup absolutely plays a role in disaster recovery (DR), but backups, restores and their associated scenarios extend beyond the scope of DR.

Backups may need to be restored in non-disaster situations, including those where RTO and RPO aren't of great concern.

*Don't confuse archival, replication, and backup. Archival is the storage of data for long-term preservation and read access. Replication is the near-real-time copying of data between replicas to support high availability and certain disaster recovery scenarios. Some requirements, such as data retention laws, may influence your strategies for all three of these concerns. Archival, replication, and backup all require separate analysis and implementation.*


### Azure backup and restore capabilities

Azure offers several backup-related services and features for various scenarios, including data in Azure as well as on-premises data. Most Azure services offer some kind of backup functionality. Here, we'll look at a few of the most popular backup-related Azure offerings.

#### Azure Backup

Azure Backup is a family of backup products that back up data to *Azure Recovery Services* vaults for storage and recovery.

*Recovery Service vaults* are storage resources in Azure that are dedicated to holding data and configuration backups for virtual machines, servers, and individual workstations and workloads.

Azure Backup serves as a general-purpose backup solution for cloud and on-premises workflows that run on VMs or physical servers. It's designed to be a drop-in replacement for traditional backup solutions that stores data in Azure instead of archive tapes or other local physical media.

Four different products and services can use Azure Backup to create backups:

- **Azure Backup Agent** is a small Windows application that backs up files, folders, and system state from the Windows VM or server on which it's installed. It works in a way that's similar to many consumer cloud-based backup solutions, but requires configuration of an Azure Recovery vault. Once you download and install it onto a Windows server or VM, you can configure it to create backups up to three times a day.

- **System Center Data Protection Manager** is a robust, fully featured, enterprise-level backup and recovery system. Data Protection Manager is a Windows Server application that can back up filesystems and virtual machines (Windows and Linux), create bare-metal backups of physical servers, and perform application-aware backup of many Microsoft server products, such as SQL Server and Exchange. Data Protection Manager is part of the System Center family of products and is licensed and sold with System Center, but it's considered part of the Azure Backup family because it can store backups in an Azure Recovery vault.

- **Azure Backup Server** is similar to Data Protection Manager, but it's licensed as part of an Azure subscription and doesn't require a System Center license. Azure Backup Server supports the same functionality as Data Protection Manager except for local tape backup and integration with the other System Center products.

- **Azure IaaS VM Backup** is a turnkey backup and restore feature of Azure Virtual Machines. VM backup supports once-per-day backups for Windows and Linux virtual machines. It supports recovery of individual files, full disks, and entire VMs, and can also perform application-consistent backups. Individual applications can be made aware of backup operations and get their filesystem resources into a consistent state before the snapshot is taken.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_40.png?)

Azure Backup can add value and contribute to the backup and restore strategy for IaaS and on-premises applications of virtually any size and shape.


#### Azure Blob storage

Azure Storage doesn't include an automated backup feature, but blobs are commonly used to back up all kinds of data from various sources. Many services that provide backup capabilities use blobs to store their data, and blobs are a common target for scripts and tools in every kind of backup scenario.

General Purpose v2 storage accounts support three different blob storage tiers of varying performance and cost. 

**Cool** storage offers the best cost-to-performance ratio for most backups, as opposed to **hot** storage, which offers lower access costs but higher storage costs. **Archive-tier** storage may be appropriate for secondary backups or backups of data with low expectations for recovery time. It's low in cost, but requires up to 15 hours of lead time to access.

**Immutable blob storage** is configurable to be non-erasable and non-modifiable for a user-specified interval. Immutable blob storage was designed primarily to fulfill strict requirements for certain kinds of data, such as financial data. It's a great option for ensuring that backups are protected against accidental deletion or modification.


#### Azure SQL Database

Comprehensive, automatic backup functionality is included with Azure SQL Database at no extra charge. Full backups are created weekly, with differential backups performed every 12 hours, and log backups created every five minutes.

Restores can be performed using the Azure portal, PowerShell, or the REST API. Backups for databases encrypted with Transparent Data Encryption, enabled by default, are also encrypted.

SQL Database backup is enterprise-grade, production ready, and enabled by default. If you're evaluating different database options for an app, it should be included as part of cost-benefit analysis, as it's a significant benefit of the service. Every app that uses Azure SQL Database should take advantage of it by including it in their disaster recovery plan and backup/restore procedures.


#### Azure App Service

Web applications hosted in the Azure App Service Standard and Premium tiers support turnkey scheduled and manual backups. Backups include configuration and file contents as well as contents of databases used by the app.

App Service backups are limited to 10 GB total, including app and database content. They're a good solution for new apps under development and small-scale apps.


### Verify backups and test restore procedures

No backup system is complete without a strategy for verifying backups and testing restore procedures. Even if you use a dedicated backup service or product, you should still document and practice recovery procedures to ensure that they're well-understood and return the system to the expected state.

***

# Microsoft Azure Well-Architected Framework - Security

## Introduction

Security is one of the most important aspects of any architecture.

Anything outside the perimeter was treated as hostile, whereas inside the wall, an organization's systems were trusted. Today's security posture is to assume breach and use the Zero Trust model.

Security professionals no longer focus on perimeter defense. Modern organizations have to support access to data and services evenly from both inside and outside the corporate firewall.

## Defense in depth

### Zero Trust model

The analyst firm Forrester Research introduced the Zero Trust model, which states that you should never assume trust but instead continually validate trust.

Most users now access applications and data from the internet, and many companies now allow users to use their own devices at work (bring your own device, or BYOD).

The Zero Trust model relies on verifiable user and device trust claims to grant access to organizational resources. No longer is trust assumed based on the location inside an organization's perimeter.

This model has forced security researchers, engineers, and architects to rethink the approach applied to security and use a layered strategy to protect their resources.


### Defense in depth: A layered approach to security

Defense in depth is a strategy that employs a series of mechanisms to slow the advance of an attack that's aimed at acquiring unauthorized access to information. Each layer provides protection so that if one layer is breached, a subsequent layer is already in place to prevent further exposure.

Microsoft applies a layered approach to security, both in its physical datacenters and across Azure services. The objective of defense in depth is to protect information and prevent it from being stolen by individuals who aren't authorized to access it. The common principles that help define a security posture are confidentiality, integrity, and availability, known collectively as CIA.

- **Confidentiality**: The principle of least privilege restricts access to information only to individuals explicitly granted access. This information includes protection of user passwords, remote access certificates, and email content.

- **Integrity**: The goal is to prevent unauthorized changes to information at rest or in transit. A common approach used in data transmission is for the sender to create a unique fingerprint of the data by using a one-way hashing algorithm. The hash is sent to the receiver along with the data. The receiver recalculates the data's hash and compares it to the original to ensure that the data wasn't lost or modified in transit.

- **Availability**: Ensure that services are available to authorized users. Denial-of-service attacks are a common cause of loss of availability to users. Natural disasters also drive system design to prevent single points of failure and deploy multiple instances of an application to geo-dispersed locations.


### Security layers

You can visualize defense in depth as a set of concentric rings, with the data to be secured at the center. Each ring adds a layer of security around the data.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_41.png?)


#### Data

In almost all cases, attackers are after data:

- Stored in a database.
- Stored on disk inside virtual machines.
- Stored on a software as a service (SaaS) application such as Microsoft 365.
- Stored in cloud storage.

The people who store and control access to data are responsible for ensuring that it's properly secured.


#### Applications

- Ensure that applications are secure and free of vulnerabilities.
- Store sensitive application secrets in a secure storage medium.
- Make security a design requirement for all application development.


#### Compute

- Secure access to virtual machines.
- Implement endpoint protection and keep systems patched and current.

#### Networking

- Limit communication between resources through segmentation and access controls.
- Deny by default.
- Restrict inbound internet access and limit outbound where appropriate.
- Implement secure connectivity to on-premises networks.

#### Perimeter

- Use distributed denial-of-service (DDoS) protection to filter large-scale attacks before they can cause a denial of service for users.
- Use perimeter firewalls to identify and alert on malicious attacks against your network.


#### Identity and access

- Control access to infrastructure (change control).
- Use single sign-on and multifactor authentication.
- Audit events and changes.


#### Physical security

Physical building security and controlling access to computing hardware within the datacenter are the first line of defense.


### Shared responsibilities

As computing environments move from customer-controlled datacenters to cloud datacenters, the responsibility of security also shifts.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_42.png?)


### Continuous improvement

The threat landscape is evolving in real time and at massive scale, so a security architecture is never complete. Microsoft and its customers need the ability to respond to these threats intelligently, quickly, and at scale.


## Identity management

### Identity as a layer of security

Digital identities are an integral part of today's business and social interactions on-premises and online. In the past, identity and access services were restricted to operating within a company's internal network. Protocols such as Kerberos and LDAP were designed for this purpose.

As your organization evaluates the capabilities of its architecture around identity, it's looking at ways to bring the following capabilities into the application:

- Provide single-sign on to application users.
- Enhance the application to use modern authentication with minimal effort.
- Enforce multifactor authentication for all sign-ins outside the company's network.
- Develop an application to allow patients to enroll and securely manage their account data.


#### Single sign-on

The more identities a user has to manage, the greater the risk of a credential-related security incident. With single sign-on, users need to remember only one ID and one password. Access across applications is granted to a single identity tied to a user, simplifying the security model. 

Using single sign-on for accounts will make it easier for users to manage their identities. It will also increase the security capabilities in your environment.

#### SSO with Azure Active Directory

**Azure AD** is a cloud-based identity service. It has built-in support for synchronizing with your on-premises Active Directory instance, or it can be used on its own. This means that all your applications, whether on-premises, in the cloud (including Microsoft 365), or even mobile, can share the same credentials. 

Administrators and developers can control access to data and applications by using centralized rules and policies configured in Azure AD.

By using **Azure AD** for SSO, you'll also have the ability to combine multiple data sources into an intelligent security graph. This security graph can help you provide threat analysis and real-time identity protection to all accounts in Azure AD, including accounts that are synchronized from on-premises Active Directory. 

By using a centralized identity provider, you'll have centralized the security controls, reporting, alerting, and administration of your identity infrastructure.


#### Synchronize directories with Azure AD Connect

Azure AD Connect can integrate your on-premises directories with Azure Active Directory. Azure AD Connect provides the newest capabilities and replaces older versions of identity integration tools such as DirSync and Azure AD Sync.

It's a single tool to provide an easy deployment experience for synchronization and sign-in.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_43.png?)

Your organization requires that authentication occurs primarily against on-premises domain controllers, but it also requires cloud authentication in a disaster recovery scenario. It doesn't have any requirements that Azure AD doesn't already support.

Your organization has made the decision to move forward with the following configuration:

- Use Azure AD Connect to synchronize groups, user accounts, and password hashes stored in on-premises Active Directory to Azure AD.

- This can be a backup if pass-through authentication is unavailable.

- Configure pass-through authentication by using an on-premises authentication agent installed on Windows Server.

- Use the seamless SSO feature of Azure AD to automatically sign in users from on-premises domain-joined computers.

  SSO reduces user friction by suppressing multiple authentication requests.


### Authentication and access

This requirement combines two aspects of the Azure AD service: multifactor authentication and conditional access policies.

#### Multifactor authentication

Multifactor authentication provides additional security for your identities by requiring two or more elements for full authentication. These elements fall into three categories:

- Something you know: A password or the answer to a security question.
- Something you have: A mobile app that receives a notification or a token-generating device.
- Something you are: Some sort of biometric property such as a fingerprint or face scan used on many mobile devices.

Azure AD has multifactor authentication capabilities built in and will integrate with other multifactor authentication providers. Basic multifactor authentication features are available to Microsoft 365 and Azure AD administrators for no extra cost.


#### Conditional access policies

Along with multifactor authentication, ensuring that additional requirements are met before granting access can add another layer of protection. Blocking logins from a suspicious IP address, or denying access from devices without malware protection, can limit access from risky sign-ins.

Azure Active Directory provides conditional access policies based on group, location, or device state. The location feature allows your organization to differentiate IP addresses that don't belong to the network, and it satisfies the security policy to require multifactor authentication from all such locations.

Your organization has created a conditional access policy that requires users who access the application from an IP address outside the company network to be challenged with multifactor authentication.

In the following illustration, user requests to access the on-premises and cloud applications are first checked against a list of conditions. The requests are either allowed access, forced to go through multifactor authentication, or blocked based on the conditions that they satisfy.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_44.png?)


### Securing applications

Azure AD Application Proxy can allow users to access the application remotely without any code changes.

**Azure AD Application Proxy** is:

- **Simple**
  You don't need to change or update your applications to work with Application Proxy.
  Your users get a consistent authentication experience. They can use the MyApps portal to get single sign-on to both SaaS apps in the cloud and your apps on-premises.

- **Secure**
  When you publish your apps by using Azure AD Application Proxy, you can take advantage of the authorization controls and security analytics in Azure. You get cloud-scale security and Azure security features like conditional access and two-step verification.
  You don't have to open any inbound connections through your firewall to give your users remote access.

- **Cost-effective**
  Application Proxy works in the cloud, so you can save time and money. On-premises solutions typically require you to set up and maintain perimeter networks, edge servers, or other complex infrastructures.


**Azure AD Application Proxy** has two components. The first is a **connector agent** that sits on a server running Windows within your corporate network. The second is an **external endpoint**, either the MyApps portal or an external URL. When a user goes to the endpoint, they authenticate with Azure AD and are routed to the on-premises application via the connector agent.


### Working with consumer identities

Azure AD B2C is an identity management service that's built on the foundation of Azure Active Directory. It enables you to customize and control how customers sign up, sign in, and manage their profiles when using your applications. This includes applications developed for iOS, Android, and .NET, among others.

Azure AD B2C provides a social identity login experience, while at the same time protecting your customer identity profile information. Azure AD B2C directories are distinct from standard Azure AD directories and can be created in the Azure portal.


## Infrastructure protection

### Role-based access control

*Role-based access control (RBAC) offers a slightly different approach*. 

Roles are defined as collections of access permissions. 

Security principals are mapped to roles directly or through group membership. 

Separating security principals, access permissions, and resources provides simplified access management and more detailed control.

On Azure, users, groups, and roles are all stored in Azure Active Directory (Azure AD). The Azure Resource Manager API uses role-based access control to secure all resource access management within Azure.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_45.png?)

#### Roles and management groups

Roles are sets of permissions, like read-only or contributor, that users can be granted to access an Azure service instance. 

Roles can be granted at the level of an individual service instance, but they also flow down the Azure Resource Manager hierarchy. 

Roles assigned at a higher scope, like an entire subscription, are inherited by child scopes, like service instances.

Management groups are an additional hierarchical level recently introduced into the RBAC model. 

Management groups add the ability to group subscriptions together and apply policy at an even higher level.

The ability to flow roles through an arbitrarily defined subscription hierarchy also allows administrators to grant temporary access to an entire environment for authenticated users. 

For example, an auditor might require temporary read-only access to all subscriptions.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_46.png?)


#### Privileged Identity Management

In addition to managing Azure resource access with RBAC, a comprehensive approach to infrastructure protection should consider including the ongoing auditing of role members as the organization changes and evolves. 

Azure AD Privileged Identity Management (PIM) is an additional paid-for offering that provides oversight of role assignments, self-service, and just-in-time (JIT) role activation.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_47.png?)

With the Azure AD PIM service, you can manage, control, and monitor access to important resources in your organization.

This includes access to resources in Azure AD; and other Microsoft Online Services, like Microsoft 365 and Microsoft Intune.


Here are some of the key features of PIM:

- Providing just-in-time privileged access to Azure AD and Azure resources

- Assigning time-bound access to resources by using start and end dates

- Requiring approval to activate privileged roles

- Enforcing Azure AD multifactor authentication to activate any role

- Using justification to understand why users activate

- Getting notifications when privileged roles are activated

- Conducting access reviews to ensure that users still need roles

- Downloading an audit history for an internal or external audit.

To use PIM, you need one of the following paid or trial licenses:

- Azure AD Premium P2

- Enterprise Mobility + Security (EMS) E5


### Providing identities to services

Azure AD has two methods : **Service principals and Managed identities for Azure services**


#### Service Principals

To understand service principals, it's useful to first understand the words identity and principal as they're used in the world of identity management.

An **identity** is just a thing that can be authenticated. Obviously, this includes users with usernames and passwords. an account is data associated with an identity.

A **principal** is an identity that acts with certain roles or claims. Consider the use of Sudo on a Bash prompt or on Windows via Run as administrator. In both of those cases, you're still signed in as the same identity as before, but you've changed your role.

A *service principal* is literally named. It's an identity that a service or application uses. Like other identities, it can be assigned roles.


### Managed identities for Azure resources

A **Managed identity** can be instantly created for any Azure service that supports it.

When you create a managed identity for a service, you're creating an account on the Azure AD tenant.

Azure infrastructure will automatically take care of authenticating the service and managing the account.


## Encryption

Data is an organization's most valuable and irreplaceable asset. Encryption serves as the last and strongest line of defense in a layered security strategy for data.


### What is encryption?

Encryption is the process of making data unreadable and unusable. To use or read the encrypted data, it must be decrypted, which requires the use of a secret key. 

There are two top-level types of encryption: *symmetric and asymmetric.*

- **Symmetric encryption** uses the same key to encrypt and decrypt the data. Consider a password manager application. You enter your passwords, and they're encrypted with your own personal key. (Your key is often derived from your master password.) When the data needs to be retrieved, the same key is used and the data is decrypted.

**Asymmetric encryption** uses a public key and private key pair. Either key can encrypt but can't decrypt its own encrypted data. To decrypt, you need the paired key. Asymmetric encryption is used for things like TLS (used in HTTPS) and data signing.


Encryption is typically approached in two ways: *encryption at rest and encryption in transit*.


### Encryption at rest

Data at rest is the data that has been stored on a physical medium. This might be data stored on the disk of a server, data stored in a database, or data stored in a storage account.


### Encryption in transit

Data in transit is the data that's actively moving from one location to another, such as across the internet or through a private network.

Encrypting data in transit protects the data from outside observers and provides a mechanism to transmit data while limiting risk of exposure.


### Encryption on Azure

#### Encrypting raw storage

Azure Storage encryption for data at rest helps you protect your data to meet your organizational security and compliance commitments.

The Azure Storage platform automatically encrypts your data with 256-bit Advanced Encryption Standard (AES) encryption before persisting it to disk and then decrypts the data during retrieval. 

This handling of encryption, encryption at rest, decryption, and key management in Azure Storage is transparent to applications that use the service. You don't need to add any code or turn on any features.

You can use Microsoft-managed encryption keys with Azure Storage encryption, or you can use your own encryption keys by selecting the option in the Azure portal.

![](https://github.com/amarnadh19/books/blob/main/images/az_well_arch_48.png?)

Azure Storage automatically encrypts data in:

- All Azure Storage services, including Azure Managed Disks, Azure Blob Storage, Azure Files, Azure Queue Storage, and Azure Table Storage

- Both performance tiers (Standard and Premium)

- Both deployment models (Azure Resource Manager and classic)


