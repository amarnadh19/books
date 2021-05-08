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
