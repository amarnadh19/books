# Azure Monitor

## Introduction

Monitoring is the act of collecting and analyzing data to determine the performance, health, and availability of your business application and the resources that it depends on. An effective monitoring strategy helps you understand the detailed operation of the components of your application. It also helps you increase your uptime by proactively notifying you of critical issues so that you can resolve them before they become problems.

Azure includes multiple services that individually perform a specific role or task in the monitoring space. Together, these services deliver a comprehensive solution for collecting, analyzing, and acting on telemetry from your application and the Azure resources that support them. They can also work to monitor critical on-premises resources to provide a hybrid monitoring environment. Understanding the tools and data that are available is the first step in developing a complete monitoring strategy for your application.

The following diagram gives a high-level view of Azure Monitor. At the center of the diagram are the data stores for metrics and logs, which are the two fundamental types of data used by Azure Monitor. On the left are the sources of monitoring data that populate these data stores. On the right are the different functions that Azure Monitor performs with this collected data. This includes such actions as analysis, alerting, and streaming to external systems.

![](https://github.com/amarnadh19/books/blob/main/images/Azure_monitor_1.png?)

Just a few examples of what you can do with Azure Monitor include:

- Detect and diagnose issues across applications and dependencies with ****.

- Correlate infrastructure issues with **VM insights and Container insights**.

- Drill into your monitoring data with **Log Analytics** for troubleshooting and deep diagnostics.

- Support operations at scale with **smart alerts and automated actions**.

- Create visualizations with Azure **dashboards and workbooks**.

- Collect data from monitored resources using **Azure Monitor Metrics**.

## Monitoring data platform

All data collected by Azure Monitor fits into one of two fundamental types, *metrics and logs*.

**Metrics** are numerical values that describe some aspect of a system at a particular point in time. They are lightweight and capable of supporting near real-time scenarios.

**Logs** contain different kinds of data organized into records with different sets of properties for each type. Telemetry such as events and traces are stored as logs in addition to performance data so that it can all be combined for analysis.

For many Azure resources, you'll see data collected by Azure Monitor right in their Overview page in the Azure portal.

Click on any of the graphs to open the data in metrics explorer in the Azure portal,

![](https://github.com/amarnadh19/books/blob/main/images/Azure_monitor_2.png?)


## Log Data

Log data collected by Azure Monitor can be analyzed with queries to quickly retrieve, consolidate, and analyze collected data.

You can create and test queries using **Log Analytics** in the Azure portal. You can then either directly analyze the data using different tools or save queries for use with **visualizations or alert rules**.

Azure Monitor uses a version of the **Kusto query language** that is suitable for simple log queries but also includes advanced functionality such as aggregations, joins, and smart analytics.

Azure Monitor uses a version of the Data Explorer query language that is suitable for simple log queries but also includes advanced functionality such as aggregations, joins, and smart analytics. You can quickly learn the query language using multiple lessons. Particular guidance is provided to users who are already familiar with SQL and Splunk.

Azure log analytics

![](https://github.com/amarnadh19/books/blob/main/images/Azure_monitor_3.png?)

## What data does Azure Monitor collect?

Azure Monitor collects data from each of the following tiers:

- **Application monitoring data**: Data about the performance and functionality of the code you have written, regardless of its platform.
Guest OS monitoring data: Data about the operating system on which your application is running. This could be running in Azure, another cloud, or on-premises.

- **Azure resource monitoring data**: Data about the operation of an Azure resource.

- **Azure subscription monitoring data**: Data about the operation and management of an Azure subscription, as well as data about the health and operation of Azure itself.

- **Azure tenant monitoring data**: Data about the operation of tenant-level Azure services, such as Azure Active Directory.

As soon as you create an Azure subscription and start adding resources such as virtual machines and web apps, Azure Monitor starts collecting data

*Activity logs* record when resources are created or modified. *Metrics* tell you how the resource is performing and the resources that it's consuming.

*Enable diagnostics* to extend the data you're collecting into the internal operation of the resources. Add an agent to compute resources to collect telemetry from their guest operating systems.

Enable monitoring for your application with *Application Insights* to collect detailed information including page views, application requests, and exceptions.

Azure Monitor can collect log data from any REST client using the Data Collector API. This allows you to create custom monitoring scenarios and extend monitoring to resources that don't expose telemetry through other sources.


## Insights

Insights provide a customized monitoring experience for particular Azure services. 

### Application Insights

Application Insights monitors the availability, performance, and usage of your web applications whether they're hosted in the cloud or on-premises.

### Container insights

Container insights monitors the performance of container workloads that are deployed to managed Kubernetes clusters hosted on Azure Kubernetes Service (AKS).

It gives you performance visibility by collecting metrics from controllers, nodes, and containers that are available in Kubernetes through the Metrics API. Container logs are also collected.

### VM insights

VM insights monitors your Azure virtual machines (VM) at scale. It analyzes the performance and health of your Windows and Linux VMs and identifies their different processes and interconnected dependencies on external processes.

## Responding to critical situations

### Alerts

*Alerts* in Azure Monitor proactively notify you of critical conditions and potentially attempt to take corrective action.

Alert rules based on metrics provide near real time alerts based on numeric values.

Alert rules in Azure Monitor use action groups, which contain unique sets of recipients and actions that can be shared across multiple rules.

### Autoscale

Autoscale allows you to have the right amount of resources running to handle the load on your application.

Create rules that use metrics collected by Azure Monitor to determine when to automatically add resources when load increases.


## Visualizing monitoring data

Visualizations such as charts and tables are effective tools for summarizing monitoring data and presenting it to different audiences.

### Dashboards

Azure dashboards allow you to combine different kinds of data into a single pane in the Azure portal.

Add the output of any log query or metrics chart to an Azure dashboard.

### Workbooks

Workbooks provide a flexible canvas for data analysis and the creation of rich visual reports in the Azure portal. 

They allow you to tap into multiple data sources from across Azure, and combine them into unified interactive experiences.

### Power BI

Power BI is a business analytics service that provides interactive visualizations across a variety of data sources. It's an effective means of making data available to others within and outside your organization.

## Integrate and export data

### Event Hub

**Azure Event Hubs** is a streaming platform and event ingestion service. 

It can transform and store data using any real-time analytics provider or batching/storage adapters. 

Use Event Hubs to stream Azure Monitor data to partner SIEM and monitoring tools.

### Logic Apps

**Logic Apps** is a service that allows you to automate tasks and business processes using workflows that integrate with different systems and services. 

Activities are available that read and write metrics and logs in Azure Monitor. This allows you to build workflows integrating with a variety of other systems.

### API

Multiple APIs are available to read and write metrics and logs to and from Azure Monitor in addition to accessing generated alerts.


