# What is Advisor and how does it work?

Azure Advisor is a free service built into Azure that provides best practice recommendations for your workloads. These recommendations are personalized and actionable.

The Azure Well-Architected Framework is a set of guiding principles that you can use to improve the quality of a workload. The framework consists of these five pillars of architecture excellence:

1) Cost Optimization

2) Security

3) Reliability

4) Performance

5) Operation Excellence

Advisor continuously analyzes your resources and cloud usage. Advisor then recommends solutions that can help you improve your workloads against these five pillars.

## Areas where Advisor can help

The Advisor dashboard gives you recommendations for each of the five categories of the Azure Well-Architected Framework:

- **Cost** -->	Helps optimize and reduce your overall Azure spend by identifying idle and underutilized resources.
- **Security** -->	Integrates with Azure Security Center to identify potential vulnerabilities that can lead to security breaches.

- **Reliability** -->	Helps to ensure and improve the continuity of your business-critical applications.

- **Operational excellence** -->	Makes recommendations for process and workflow efficiency, resource manageability, and deployment best practices.

- **Performance** -->	Helps improve the speed and responsiveness of your business-critical applications.

## How does Advisor work?

Advisor analyzes your resource configuration and usage telemetry and then gives you actionable recommendations that can help you improve the cost effectiveness, performance, reliability, and security of your Azure resources, as well as your operational excellence.

Advisor operates at the subscription and resource level, either in aggregate or individually. 

You can access Advisor recommendations as Owner, Contributor, or Reader of a subscription or resource. These levels of access also apply to partners who manage Azure resources on your behalf.

## Examples of Advisor recommendations

Advisor gives you several recommendations for each of these categories. Here are just a few examples for each category, most of which are fairly self-explanatory:

### Cost

- Resize or shut down underutilized virtual machine instances.
- Eliminate unprovisioned ExpressRoute circuits.
- Delete or reconfigure idle virtual network gateways.

### Reliability

- Ensure application gateway fault tolerance.
- Enable backup to protect your virtual machine data from accidental deletion.
- Configure Traffic Manager endpoints for resiliency.

### Operational excellence

- Create Azure Service Health alerts to notify you when Azure problems affect you.
- Design your storage accounts to prevent reaching the maximum subscription limit.
- Check if validation environment is enabled.

### Performance

- Improve App Service performance and reliability.
- Use managed disks to prevent disk I/O throttling.
- Improve MySQL connection management.

### Security

- Management ports of virtual machines should be protected with just-in-time network access control.
- FTPS should be required in your web app.
- Container images should be deployed from trusted registries only.


# Understand your optimization posture with Advisor Score

## What is Advisor Score?

Advisor aggregates its findings into a single number – Advisor Score.

Advisor Score is a rating of your Azure subscriptions on a scale from 0% to 100% to help you understand how well the resources in those subscriptions are optimized, based on our documented best practices.




# Reduce service costs by using Azure Advisor

Azure Advisor helps you optimize and reduce your overall Azure spend by identifying idle and underutilized resources. You can get cost recommendations from the Cost tab on the Advisor dashboard.

## Optimize virtual machine spend by resizing or shutting down underutilized instances

You can often save money by managing the size and number of your virtual machines.

The recommended actions are shut down or resize, specific to the resource being evaluated.

The advanced evaluation model in Advisor considers shutting down virtual machines when all of these statements are true:

- P95th of the maximum value of CPU utilization is less than 3%.

- Network utilization is less than 2% over a seven-day period.

- Memory pressure is lower than the threshold values