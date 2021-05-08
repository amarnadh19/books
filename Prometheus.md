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


## Understanding Metrics Collection

The process by which metrics are by monitoring systems can be generally be divided into two approaches: *Push* and *pull*.


## An overview of the two collection approaches

In *push-based* monitoring systems, emitted metrics or events are sent either directly from the producting application or from a local agent to the collecting service like so:

![Push-based monitoring system](https://github.com/amarnadh19/books/blob/main/images/pro_image_1.png?)

Systems that handle raw event data generally prefer push since the frequency of envent generation is very high.

Some examples that use this approach include Riemann, StatsD, and the Elasticsearch, logstash and the Kibana (ELK) stack.

That is not to say that only these types of systems use push. Some monitoring systems such as Graphite, OpenTSDB, and the Telegraf, InfluxDB, Chronograph, and Kapacitor (TICK) stack have been designed using this approach. Even good old Nagios supports push through the Nagios Service Check Acceptor (NSCA), commonly known as passive checks:

![Pull-based monitoring system](https://github.com/amarnadh19/books/blob/main/images/pro_image_2.png?)

In contract, Pull based monitoring systems collect metrics directly from applications or from proxy processes that make those metrics available to the system. 

Some notable monitoring software that uses pull are Nagios and Nagios-style systems (Icinga, Zabbix, Zenoss, and Sensu, to name a few). Prometheus is also one of those that embraces the pull approach and is very opinionated about this.


## Push Vs Pull

The main point of contention is usually about target discover.


### Push-Based systems

In *push-based systems*, the monitored hosts and services make themselves known by reporting to the monitoring system. The advantage here is that no prior knowledge of new systems is required for them to be picked up. However, this means that the monitoring service's location needs to be propagated to all targets, usually with some form of configuration management. Staleness is a big drawback of this approach: if a system hasn't reported in for some time, does that mean it's having problems or was it purposely decommissioned?

Furthermore, when you manage a distributed fleet of hosts and services that push data to a central point, the risk of a thundering herd (overload due to many incoming connections at the same time) or a misconfiguration causing an unforeseen flood of data becomes much more complex and time-consuming to mitigate.


### Pull-Based systems

In *pull-based monitoring*, the system needs a definitive list of hosts and services to monitor so that their metrics are ingested.

Having a central source of truth provides some level of assurance that everything is where it's supposed to be, with the drawback of having to maintain said source of truth and keeping it updated with any changes. With the rapid rate of change in today's infrastructures, some form of automated discovery is needed to keep up with the full picture. Having a centralized point of configuration enables a much faster response in the case of issues or misconfigurations.

In the end, most of the drawbacks from each approach can be reduced or effectively solved by clever design and automation.

There are other more important factors when choosing a monitoring tool, such as flexibility, ease of automation, maintainability, or broad support for the technologies being used.

*Even though Prometheus is a pull-based monitoring system, it also provides a way of ingesting pushed metrics by using a gateway that converts from push to pull. This is useful for monitoring a very narrow class of processes*.


## What is a measure?

When planning metrics collection, there is a question that's bound to come up, which is defining what metrics to observe. To answer this question, we should turn to the current best practices and methodologies.


## Google's four golden signals

Google's rationale regarding monitoring is quite simple. It states, pretty straightforwardly, that the four most important metrics to keep track of are the following:

    1) Latency: The time required to serve a request
    
    2)Traffic: The number of requests being made
    
    3) Errors: The rate of failing requests
    
    4) Saturation: The amount of work not being processed, which is usually queued

## Brendan Gregg's USE method

Brendan's method is more machine-focused and it states that for each resource (CPU, disk, network interface, and so on), the following metrics should be monitored:

    - Utilization: Measured as the percentage of the resource that was busy
    
    - Saturation: The amount of work the resource was not able to process, which is usually queued
    
    - Errors: Amount of errors that occurre


## Tom Wilkie's RED method

The RED method is more focused on a service-level approach and not so much on the underlying system itself. Obviously, being useful to monitor services, this strategy is also valuable to predict the experience of external clients. If a service's error rate increases, it is reasonable to assume those errors will impact, directly or indirectly, on the customer's experience. These are the metrics to be aware of:

    - Rate: Translated as requests per second
    
    - Errors: The amount of failing requests per second
    
    - Duration: The time taken by those requests

***

# A overview of Prometheus Ecosystem

## Metrics Collection with Prometheus

Prometheus is a time series-based, open source monitoring system. It collects data by sending HTTP requests to hosts and services on metrics endpoints, which it then makes available for analysis and alerting using a powerful query language. 

Even though Prometheus has graduated with the Cloud Native Computing Foundation (CNCF) by demonstrating stability, maturity, and solid governance, it is still evolving at a very rapid pace.

At the time of writing this book, the latest version is 2.26.0


## High-level Overview of the Prometheus Architecture

The Prometheus ecosystem is composed of several components, each with its own responsibility and clearly defined scope. Prometheus itself is essential as it sits squarely in the middle of most interactions, but many components are in fact optional, depending on your monitoring needs.

![High level overview of the main components in the Prometheus echosystem](https://github.com/amarnadh19/books/blob/main/images/pro_image_3.png?)

- The Prometheus server collects time series data, stores it, makes it available for querying, and sends alerts based on it.

- The Alertmanager receives alert triggers from Prometheus and handles routing and dispatching of alerts.

- The Pushgateway handles the exposition of metrics that have been pushed from short-lived jobs such as cron or batch jobs.

- Applications that support the Prometheus exposition format make internal state available through an HTTP endpoint.

- Community-driven exporters expose metrics from applications that do not support Prometheus natively.

- First-party and third-party dashboarding solutions provide a visualization of collected data.

The prometheus server has its own internal processes, such as recording rules and service discovery.

*Prometheus was originally created by Matt T. Proud and Julius Volz while working at SoundCloud. It was inspired by Google's Borgmon, which influenced a lot of its earlier design: scraping plain text from metrics endpoints; exporters as proxies for metrics collection; time series as multi-dimensional vectors, which can then be transformed and filtered; and the use of ruleset evaluations for recording and alerting, among other features.*


## Exposing internal state with exporters

Not all applications are built with Prometheus-compatible instrumentation. Sometimes, no metrics are exposed at all. In these cases, we can rely on exporters

![High level overview of an exporter](https://github.com/amarnadh19/books/blob/main/images/pro_image_4.png?)

An exporter is nothing more than a piece of software that collects data from a service or application and exposes it via HTTP in the Prometheus format. Each exporter usually targets a specific service or application and as such, their deployment reflects this one-to-one synergy.

Nowadays, you can find exporters for pretty much any service you need, and if a particular third-party service doesn't have an exporter available, it's quite simple to build your own.


## Exporter fundamentals

When the exporter starts, it binds to a configured port and exposes the internal state of whatever is being collected in an HTTP endpoint of your choosing (the default being /metrics).

The instrumentation data is collected when an HTTP GET request is made to the configured endpoint.

For Example,  node exporter, one of the most commonly used exporters, relies on a number of kernel statistics to present data such as disk I/O, CPU, memory, network, filesystem usage, and much, much more. Every single time that endpoint is scraped, the information is quickly gathered and exposed in a synchronous operation.

The Http GET request that is made by the Prometheus server to the observed system for metric collection is called a **scrape**.

If you are the one writing the service, the best option is to instrument the code directly using a Prometheus client library. There are official client libraries available for the following programming languages:

- Go
- Java/JVM
- Python
- Ruby

There are community-driven client libraries for the following programming languages:

- Bash
- C++
- Common Lisp
- Elixir
- Erlang
- Haskell
- Lua for NGINX
- Lua for Tarantool
- .NET
- C#
- Node.js
- Perl
- PHP
- Rust

Usually, exporters are very light and the performance footprint is mostly negligible but, as always, there are exceptions for this rule.


## Alert routing and management with Alert Manager

Alertmanager is the component from the Prometheus ecosystem that's responsible for the notifications that are triggered by the alerts that are generated from the Prometheus server.

As such, its availability is of the essence and the design choices reflect this need. It's the only component that's truly conceived to work in a highly available cluster setup, and uses gossip as the communication protocol

![High level overview of Alertmanager](https://github.com/amarnadh19/books/blob/main/images/pro_image_5.png?)

At a very high level, Alertmanager is a service that receives HTTP POST requests from Prometheus servers via its API, which it then deduplicates and acts on by following a predefined set of routes.

AlertManager also exposes a web interface to allow, for instance, the visualization and silencing of firing alerts of applying inhibition rules for them.

One of the core design choices is to value delivery over deduplication. This means that if a network partition occurs between a cluster of Alertmanager instances, notifications will be sent from both sides of the partition.


### Alerting Routes

A route, in its essence, can be seen as a tree-like structure. If an incoming alert has a specific payload that triggers a particular route (branch in tree), a pre-defined integration will be invoked.

There are multiple out-of-the-box integrations available for the most common use cases, such as:

- Email
- Hipchat
- PagerDuty
- Slack
- Opsgenie
- VictorOps
- WeChat

There's also the webhook integration that issues an HTTP POST request with the JSON payload of the firing alert to an endpoint of your choosing.


## Visualizing your data

Data visualization is one of the simplest ways to produce or consume information. Prometheus exposes a well-defined API, where PromQL queries can produce raw data for visualizations.

Currently, the best external software for visualization is Grafana.

The Prometheus server also ships with two internal visulizations components:

- Expression Browser :-  Here, you can run PromQL directly to quickly query data and visualize it instantly:

![The Prometheus expression browser interface](https://github.com/amarnadh19/books/blob/main/images/pro_image_6.jpg?)

- Consoles :- These are web pages that are built using the Golang templating languages and are served by the Prometheus server itself. This approach allows you to have pre-defined data visualization interfaces without you having to constantly type PromQL:

![The Prometheus console interface](https://github.com/amarnadh19/books/blob/main/images/pro_image_7.png?)


#### Note Architecture in Detail (Source from Prometheus site)
    
![The Prometheus Architecture in detail](https://github.com/amarnadh19/books/blob/main/images/pro_architecture.png?)


***

# Prometheus Metrics Fundamentals

Metrics are the core resources that the Prometheus stack ingests to provide you with usefull information. Understand them correctly is essential to fully utilize, manage, or even extend the realm of possibilities this stack has to offer.


## Understanding Prometheus data Model

To understand the Prometheus data model, we need to go through what makes a time series and the storage of such data.


### Time Series Data

Time series data can usually be defined as a sequence of numerical data points that are indexed chronologically from the same source.

In the scope of Prometheus, these data points are collected at a fixed time interval.

As such, this kind of data, when represented in graphical form, will most commonly plot the evolution of the data through time, with the x axis being time and the y axis being the data value.


### Time series databases

It all starts with the need to collect, store, and query measurements over time. Nothing prevents you from using standard relational or NoSQL databases to store time series data.

As such, modern time series databases store the following components:

    - A timestamp
    - A value
    - Some context about the value, encoded in a metric name or in associated key/value pairs


An abstract example of data that fits this time series database specification is as follows:

```
timestamp=1544978108, 
company=ACME, 
location=headquarters, 
beverage=coffee, 
value=40172
```


## Prometheus local storage

Local storage is the standard approach for storing data in Prometheus. 

At a very high level, Prometheus storage design is a combination of an index implementation using posting lists for all currently stored labels with their values, and its own time series data format.


### Data Flow

The way Prometheus stores collected data locally can be seen as a three part process.


### Memory

The freshest batch of data is kept in memory for upto two hours. This approach dramatically reduces disk I/O two fold; the most recent data is available in memory, making it blazingly fast to query; and the chunks of data are created in memory, avoiding constant disk writes.


### Write ahead log

While in memory, data is not persisted and could be lost if the process terminates abnormally. To prevent this scenario, a write-ahead log (WAL) in disk keeps the state of the in-memory data so that it can be replayed if Prometheus, crashes or restarted.


### Disk

After two-hour time window, the chunks get written to disk. These chunks are immutable and, even though data can be deleted, it is not an atomic operation.


### Layout

The way data gets stored in Prometheus is organized into a series of directories (Blocks) containing the data chunks, the LevelDB index for that data, a ``` meta.json ``` file with human-readable information about the block. Each one of these blocks represents a database.

![Example directory structure](https://github.com/amarnadh19/books/blob/main/images/pro_image_8.png?)


## Prometheus Data Model

Prometheus stores data as time series, which includes key/value pairs known as labels, a timestamp, and finally a value.


### Notation

A time series in Prometheus is represented as follows:

``` <metric_name>[{<label_1="value_1">,<label_N="value_N">}] <datapoint_numerical_value> ```

### Metric names

Even though this is an implementation detail, a metric name is nothing more than the value of a special label called ``` __name__```. So, if you have a metric named ``` beverages_total ```, internally, it's represented as ``` __name__=beverages_total ```. Keep in mind that labels surrounded by ``` __ ``` are internal to Prometheus, and any label prefixed with ```__ ``` is only available in some phases of the metrics collection cycle.

The combination of labels (key/values) and the metric name defines the identity of a time series.

Every metric name in Prometheus must match the following regular expression:

``` a-zA-Z_:][a-zA-Z0-9_:]* ```


### Metric Labels

Labels, or the key/value pairs associated with a certain metric, add dimensionality to the metrics.

While label values can be full UTF-8, Labels name have to match a regular expression to be considered valid; 

``` for example,  [a-zA-Z0-9_]* ```

