# Monitoring Fundamentals

Foundation of some key concepts of monitoring.

## Definition of Monitoring

A consensual definition of monitoring is hard to come by because it quickly shifts between industry or even job specific contexts.

The diversity of viewpoints, the components comprising the monitoring system, and even how the data is collected or used are all factors that contribute to the struggle of reaching a clear definition. 


## The value of Monitoring

With the growing complexity of infrasturctures, exponentially driven by the adoption microservices-oriented architectures, it has become critical to attain a global view of all the different components of an infrastructure. 

Nowadays, it is expected that monitoring will keep track of data from those components. However, data might come in several forms, allowing it to be used for different purposes.

Alerting is one of the standard uses of monitoring data, but the application of such data can go for beyond it.

You can look at monitoring as a source of information for maintaining healthy systems, production and business wise.


## Organizational Contexts

Looking into an organizational context, roles such as system administrators, quality assurance engineers, siteReliability Engineers (SREs), or product owners have different expectations from monitoring.

    1) System administrators are interested in high-resolution, low-latency, and high-diversity data. For a system administrator, the main objective of monitoring is to obtain visibility across the infrastructure and manage data from CPU usage to Hypertext Transfer Protocol (HTTP) request rate so that problems are quickly discovered and the root causes are identified as soon as possible. In this approach, exposing monitoring data in high resolution is critical to be able to drill down into the affected system. If a problem is occurring, you don't have the privilege to wait several hours for your next data point, and so data has to be provided in near real time or, in other words, with low latency. Lastly, since there is no easy way to identify or predict which systems are prone to be affected, we need to collect as much data as possible from all systems; namely, a high diversity of data.

    2) Quality assurance engineers are interested in high-resolution, high-latency, and high-diversity data. Besides being important for quality assurance engineers to have high resolution monitoring data collected, which enables a deeper drill down into effects, the latency is not as critical as it is for system administrators. In this case, historical data is much more critical for comparing software releases than the freshness of the data. Since we can't wholly predict the ramifications of a new release, the available data needs to be spread across as much of the infrastructure as possible, touching every system the software release might use and invoke it or generally interact with it (directly or indirectly), so that we have as much data as possible.

    3) SREs focused on capacity planning are interested in low-resolution, high-latency, and high-diversity data. In this scenario, historical data carries much more importance for SREs than the resolution that this data is presented in. For example, to predict the increase in infrastructure, it is not critical for a SRE to know that some months ago at 4 A.M., one of the nodes had a spike of CPU usage reaching 100% in 10 seconds, but is useful to understand the trend of the load across the fleet of nodes to infer the number of nodes required to handle new scale requirements. As such, it is also important for SREs to have a broad visualization of all the different parts of the infrastructure that are affected by those requirements to predict, for example, the amount of storage for logs, network bandwidth increase, and so on, making the high diversity of monitoring data mandatory.

    4) Product owners are interested in low-resolution, high-latency, and low-diversity data. Where product owners are concerned, monitoring data usually steps away from infrastructure to the realm of business. Product owners strive to understand the trends of specific software products, where historical data is fundamental and resolution is not so critical. Keeping in mind the objective of evaluating the impact of software releases on the customers, latency is not as essential for them as it is for system administrators. The product owner manages a specific set of products, so a low diversity of monitoring data is expected, comprised mostly of business metrics.

The following table sums up the previous examples in a much more condensed form:

|                           | Data resolution   | Data Latency      |  Data diversity   |
| --------------            | ---------------   | ------------      |  ---------------  |
| Infrasturcture Alerting   | High              | Low               |  High             |
| Software release View     | High              | High              |  High             |
| Capacity Planning         | Low               | High              |  High             |
| Product/Business view     | Low               | High              |  Low              |


## Monitoring Components

The same way the monitoring definition changes across contexts, its components follow the same predicament. 

Components can be given below topics:

    1) Metrics : This exposes a certain system resources, application action, or business characteristic as specific point in time value. This information is obtained in an aggregated form

    2) Logging : Containing much more data than a Metric, this manifests itself as an event from a system or application, containing all the information that is produced by such an Event.

    3) Tracing : This is a special case of logging where a request is given a unique identifier so that it can be tracked during its entire life cycle across every system. Due to increase of the dataset with the number of requests, it is a good idea to use samples instead of tracking all requests. 

    4) Alerting : This is the continuous threshold validation of metrics or logs, and fires an action or notification in the case of a transgression of the said threshold.

    5) Visualization : This is a graphical representation of metrics, logs, or traces. 


Recently, the term monitoring has been overtaken by a superset called **observability**, which is regarded as the evolution of monitoring, or a different wrapping to spring a hype and revive the concept.


## White box versus blackbox monitoring

There are many ways we could go about monitoring, but they largely fall into two main categories, i.e., **blackbox** and **whitebox** monitoring.

In *Blackbox* monitoring, the application or host is observed from the outside and, consequently, this approach can be fairly limited. Checks are made to assess whether the system under observation responds to probes in a known way:

    - Does the host respond to ICMP echo requests?
    - is a given TCP port Open?
    - Does the application respond with the correct data and status code when it receives a specific HTTP requests?
    - Is the process for a specific application running in its host?

In *Whitebox* monitoring, the system under observation surfaces data about its internal state and the performance of critical sections.  This type of intospection can be very powerful as it exposes the operating telementry, and consequently the health, of the different internal components.

    - Exported through logging: For instance, an HTTP server's access log can be processed to monitor requests rates, latencies and error percentages.

    - Emitted as structured Events: This approach is similar to logging but instead of being written to disk, the data is sent directly to processing systems for analysis and aggregations.

    - Maintained in memory as aggregates: Data in this format can be hosted in an endpoint or read directly from command-line tools. 

Probing can be your last line of defence - if all else fails, you can rely on blackbox monitoring to asses availability.


## understanding Metrics Collection

The process by which metrics are by monitoring systems can be generally be divided into two approaches: *Push* and *pull*.


## An overview of the two collection approaches

![first image] (pro_image_1.png)
