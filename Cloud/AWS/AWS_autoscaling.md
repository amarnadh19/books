# Autoscaling

Auto scaling refers to a cloud computing technique for allocation computational resources on demand.

Autoscaling and load balancing are related since you can scale application based on load capacity.


## What is AWS Autoscaling
AWS Auto Scaling is an Amazon service adept at automatically monitoring and adjusting compute resources to maintain a steady, predictable performance for your applications hosted in the AWS. It increases the available processing power or storage resources for applications as demand rises and decreases when they are no longer required. When you use AWS Auto Scaling, your applications are constantly monitored, and their capacity is changed automatically to deliver consistent, predictable performance at the lowest possible cost.

![](https://github.com/amarnadh19/books/blob/main/images/AWS-auto-scaling1.png?)

AWS Auto Scaling is different from the Auto Scaling tool provided by the cloud provider, which can only scale individual services. This solution, which contains two distinct APIs, allows for step scaling policies and scheduled scaling; none of these features are supported by AWS Auto Scaling. In addition, Amazon Web Services (AWS) also provides support for EC2 Auto Scaling – a feature that enables you to scale groups of EC2 instances.


## Benefits of Auto Scaling

### Reduced pricing

Automatic resource scaling allows resources to be increased only when they are required and decreased when traffic decreases. It is one method for companies to minimize their cloud computing expenses.

AWS Autoscaling is a free service that reduces the number of resources that are not in use, thus assisting in averting overspending.

### Automation

autoscaling is automated and policy-driven means that it is more efficient than manual scaling since it activates only when required.


### Improved Fault Tolerance

In using autoscaling, the health and performance of a workload are continuously evaluated to replace and scale resources automatically as needed when workload increases.


### Monitoring

If you use AWS Auto Scaling, your applications are constantly tracked, and their capacity is changed automatically to deliver consistent, predictable performance at the lowest feasible cost.

### Service Availability

In the case of a traffic surge, autoscaling may help to guarantee that services remain available.

### Manage Resource Provisioning

You can take advantage of Autoscaling to manage resource provisioning for all of your EC2 auto-scaling groups, as well as database tables being used in your application.

### Better Reliability of Resources

AWS Auto Scaling is adept at identifying and tracking the performance of your scalable resources, i.e., resources that can scale. Such resources can span various cloud services as well. These resources include the following:

```
Amazon Elastic Container Service (ECS) Components
Aurora Replicas or Clusters
Auto Scaling Groups
DynamoDB Global Secondary Indexes or Tables
Elastic Compute Cloud (EC2)
EC2 Spot Fleets
```

## Autoscaling Services on AWS Cloud Platform

- **EC2 Instance Auto Scaling**: This helps you maintain the number of Amazon EC2 instances required by your application to meet incoming traffic demands. You may build EC2 auto-scaling groups that are made up of EC2 instances, and you can define minimum and maximum scaling thresholds for each of these groups.

- **Amazon EC2 Spot Fleet Requests**: A spot fleet comprises a group of EC2 spot instances. AWS Auto Scaling can adjust the capacity of Spot Fleet based on demand automatically.

- **Elastic Container Service (ECS) Auto Scaling**: AWS Auto Scaling automatically enhances or reduces the capacity of ECS container tasks on Amazon Web Services.

- **DynamoDB Auto Scaling**: This creates scaling policies for the table or secondary index. As an example, you might want to indicate whether you want to increase read and write capacity and the maximum and minimum provided capacity units. You can also indicate the maximum and the minimum number of provisioned capacity units for a table or an index.


## Types of Autoscaling

- **Reactive:** When using a reactive autoscaling method, resources are scaled up and down in response to surges in traffic.

This technique is strongly associated with the real-time monitoring of available resources. *There is often a cooldown period involved, which is a predetermined time during which resources are maintained at maximum capacity — even when traffic decreases — to cope with any further incremental traffic surges.*

- **Predictive:** A predictive autoscaling method uses machine learning and artificial intelligence tools to evaluate traffic loads and anticipate when you’ll need more or fewer resources.

Predictive scaling analyzes each resource’s past workload and predicts the anticipated load for the following two days using machine learning.

Predictive autoscaling applies predictive analytics, including past usage data and current usage patterns, to scale depending on future demand projections automatically.

- **Scheduled:** Users may choose the time range based on which additional resources will be added. Scheduled autoscaling is a hybrid approach that operates in real-time, predicts known changes in traffic loads, and responds to such changes at predetermined intervals.

Scheduled scaling is most effective when there are predictable traffic drops or spikes at specific times of the day, but the changes are usually very abrupt.

- **Manual Scaling:** In Manual Scaling, the number of instances is manually adjusted. You can manually increase or decrease the number of instances through a CLI or console. Manual Scaling is a good choice when your user doesn’t need automatic Scaling.

- **Dynamic Scaling:** This is yet another type of Auto Scaling in which the number of EC2 instances is changed automatically depending on the signals received. Dynamic Scaling is a good choice when there is a high volume of unpredictable traffic.


## What is an AWS Auto Scaling Plan?

In AWS, a scaling plan is a set of instructions for scaling up or scaling down your resources. A scaling plan is one of the most important components of AWS Auto Scaling, and it should not be overlooked. Typically, you would configure a set of instructions in a scaling plan for scaling your resources here.

AWS Auto Scaling analyses each resource and makes suggestions for scaling strategies that are tailored based on the resource requirements. After a scaling plan has been created, AWS Auto Scaling combines dynamic and predictive scaling techniques and executes it.

A scaling strategy instructs AWS Auto Scaling on making the most of the resources available in your scaling plan to achieve the best possible usage. You have the option of optimizing for availability, cost, or a combination of the two. You may design your custom strategy based on the metrics and thresholds that you provide as an alternative. You may also create different strategies for each resource or resource type that you want to use.

You can take advantage of scaling strategy to optimize resources in your application and create your own scaling strategy based on the required metrics and thresholds. You may create a separate scaling strategy for each group of resources by using AWS CloudFormation or adding tags to your AWS resources.


## Scaling Plans Offered by AWS

- **Maintaining the current instance level at all times**:  Using this scaling plan, the user may create an AWS auto-scaling group always to have a specific number of active instances.

- **Manual scaling:** This scaling plan enables the user to define the required capacity of AWS auto-scaling groups. The auto-scaling service takes care of generating and terminating instances automatically.

- **Scaling on a schedule:** This scaling strategy is beneficial when the user can forecast when the application’s traffic will grow. In such situations, the user may choose a time for AWS auto-scaling to run.

- **Scaling according to demand:** This scaling plan enables the user to specify scaling criteria such as CPU and Memory utilization, and so on.


## Components of Auto Scaling in AWS

- **AMI:** An AMI, an acronym for Amazon Machine Image, is an executable image of your EC2 Instance that you may use to create new instances on Amazon’s cloud computing platform.

- **Load Balancer:** A load balancer can automatically detect the traffic flowing through it and route traffic based on pre-defined rules.

Load balancing is a process that can distribute the traffic among instances, optimize resource use, maximize throughput, minimize response time, improve the application’s throughput, and ensure that a particular resource is not overloaded.

- **EC2 Instance:** Essentially, an EC2 instance, also known as an Elastic Compute Cloud instance, is a virtual server that can serve an unlimited set of virtual machines and is used for running applications on the Amazon Web Services (AWS) infrastructure.

- **Autoscaling Groups:** An Auto Scaling Group is a collection of Amazon EC2 instances that have been logically grouped for automatic scaling.
