# Azure Cache 

## Introduction

Databases form the cornerstone of many enterprise apps. Making your databases as responsive as possible is vital for modern app development. Azure Cache for Redis can help you improve your apps' performance and scalability by copying frequently accessed data and storing it in memory.

As the following graphic illustrates, Azure Cache for Redis can help improve performance in apps that interface with many database solutions, including Azure SQL Database, Azure Cosmos DB, and Azure Database for MySQL.

![](https://github.com/amarnadh19/books/blob/main/images/az_cache1.png?)


## What is Azure Cache for Redis?

### What is Redis?

Redis is a widely used, open-source caching solution. It's a key-value datastore that runs in memory, so it's very responsive.

Typically, organizations use Redis to complement their database apps. Combining Redis with back-end databases enables you to significantly improve your apps' performance.


### What should a caching solution do?

Any caching solution should address four key requirements:

- **Performance.** The primary requirement for any caching solution is to improve performance, even under high loads. Ideally, it should increase throughout and reduce latency.

- **Scalability.** A system must respond to load changes promptly. Scaling should be automatic and occur without downtime.

- **Availability.** Any caching solution must be highly available. This helps ensure that your apps can deliver at peak performance, even if component failures occur.

- **Support for geographic distribution.** It's essential that a caching solution provides the same performance and scaling benefits everywhere in the world. This can be challenging if your data is geographically dispersed.


### Azure Cache for Redis definition

Azure Cache for Redis enables you to implement Redis as a fully managed service.

    Note:

    Azure Cache for Redis offers both Redis open-source (OSS Redis) and a commercial product from Redis Labs (Redis Enterprise) as a managed service, depending on the tier you select.

**Azure Cache for Redis provides the following application architecture patterns:**

- **Data cache.** Databases often are too large to load directly into cache. That's why it's common to use the *cache-aside pattern*. It loads data into the cache only as needed.

- **Content cache.** Most webpages contain static items, such as headers, footers, and banners. These items don't change very often. By using an *in-memory content cache*, you can provide quick access to static content as compared to accessing back-end datastores.

- **Session store.** This pattern is often used with shopping carts or other data based on user history data. The reason is that web applications often associate these with user cookies. Storing too much data in a cookie can adversely affect performance. The reason is that apps often use cookies to query a back-end database for user data. Using an *in-memory cache* to store user-session information is faster than working with the backend database.

- **Job and message queuing.** Apps frequently add tasks to a queue. This occurs when the tasks might take a long time to run. If a task contains long-running operations, they're typically queued to run in sequence. *Azure Cache for Redis* provides publish/subscribe, message streaming, or queue architectures to support this application pattern.

    Note

    Longer running operations are queued to process in sequence, often by another server.

- **Distributed transactions.** Sometimes apps require a series of commands to run on a back-end datastore as a single operation. *Azure Cache for Redis* supports running a batch of commands as a single transaction.

    Note

    All commands must either succeed or be rolled back to the initial state.

## Azure Cache for Redis tiers

You can select from the following five Azure Cache for Redis tiers:

- The Basic tier runs on a single virtual machine (VM) and doesn't include a service-level agreement (SLA). This tier is based on an OSS Redis cache.

- The Standard tier runs on two replicated VMs and is based on an OSS Redis cache.

    Note:

    Standard and Basic are single-node caches. You should consider these tiers only for noncritical workloads.

- The Premium tier is deployed on more powerful VMs. This tier offers features such as higher throughput, lower latency, and better availability. This tier is based on an OSS Redis cache.

- The Enterprise tier offers higher availability than the Premium tier and a high-performance cache that's powered by Redis Labs' Redis Enterprise software.

- The Enterprise Flash tier offers a cost-effective alternative to the Enterprise tier and is also powered by Redis Labs' Redis Enterprise software. This tier extends Redis data storage to nonvolatile memory, which reduces overall memory cost per gigabyte (GB).

All tiers support the following features:

- Data encryption in transit
- Network isolation
- Scaling

The Premium, Enterprise, and Enterprise Flash tiers also support other advanced features, including:

- **Clustering.** Provides for high-availability and load distribution.

- **Data persistence.** Allows you to persist data in Redis. This enables you to take snapshots and back up data. You can then load these snapshots should a hardware failure occur.

- **Zone redundancy.** Provides higher resilience and availability because the VMs are spread across multiple availability zones.

- **Geo-replication.** Links two Azure Cache for Redis instances and creates a data-replication relationship. This replication provides a potential disaster-recovery solution.

- **Import/Export.** Enables you to import data into, or export data from, Azure Cache for Redis. You can import or export an Azure Cache for Redis Database (RDB) snapshot from a premium cache to an Azure Storage Account blob.


The following features are only available in the Enterprise tiers:

- **RediSearch.** Provides a powerful indexing and querying engine with a full-text search engine.

- **RedisBloom.** Provides support for probabilistic data structures.

- **RedisTimeSeries.** Enables you to ingest and query large quantities of data with very high performance.

- **Active Geo-Replication.** Implements conflict-free replicated data types, and supports writes to multiple cache instances. Manages merging of changes and conflict resolution when necessary.


## How Azure Cache for Redis works

Azure Cache for Redis use-cases:

- Distributed cache
- Session store
- Message broker
- Cloud migration

### Distributed cache

The distributed cache use-case in Azure Cache for Redis helps improve your apps' response times by copying frequently-accessed data to a cache.

This cache has lower latency and provides for higher throughput than the primary datastore.

The distributed cache feature:

- Accelerates application responsiveness.
- Helps reduce load on primary datastores and compute resources.
- Integrates with many Azure databases, including Azure SQL and Azure Cosmos DB.

You can use distributed cache to:

- Manage spikes in traffic.
- Cache and provide commonly accessed data to users.
- Help reduce compute load on your databases.
- Locate content geographically closer to users.
- Provide for output caching.

As the following graphic illustrates, Azure Cache for Redis can help improve performance in apps that interface with many database solutions, including Azure SQL Database, Azure Cosmos DB, and Azure Database for MySQL.

![](https://github.com/amarnadh19/books/blob/main/images/az_cache1.png?)


### Session store

Your session-oriented apps require the ability to store and access temporary session data when users sign in and remain active on your apps.

The session store use-case in Azure Cache for Redis:

- Manages up to hundreds of thousands of simultaneous users.
- Makes data-replication options available to help provide for maximum reliability.
- Helps reduce costs, as it's typically more cost-effective and scalable than alternative database or storage options.

You can use session store to:

- Help facilitate eCommerce shopping carts.
- Store user cookies.
- Maintain user login and session state data.
- Enable IoT telemetry.

### Message broker

Apps built on microservices often need to asynchronously communicate. 

Azure Cache for Redis can implement a publish/subscribe or queue architecture that can help enable fast and reliable communication between these microservices. 

The Azure Cache for Redis message broker:

- Provides a temporary data store with minimal overhead and cost.
- Supports TLS encryption for data in transit.
- Provides network isolation for secure communication between your services.

You can use the message broker use-case to:

- Publish news, financial data, or application updates to users.
- Manage chat messages.
- Enable communication between microservices.

In the following graphic, a number of group chats, notifications, and stock quotes are occurring. They're connected to the message-broker feature in Azure Cache for Redis. This feature, in turn, connects to Azure API Apps instances and Azure web apps. These elements provide access to the group chats, notifications, and stock quotes for connected client devices.

![](https://github.com/amarnadh19/books/blob/main/images/az_cache2.png?)


### Cloud migration

If you're moving from an on-premises cache to a managed service, a critical factor is how to move content to the managed service. Azure Cache for Redis helps migrate data to the cloud and also:

- Enables both import and export of RDB files.

- Provides compatibility with open-source Redis to help simplify migration.

- Provides a fully managed service that manages:

  - Patching
  - Updates
  - Provisioning
  - Scaling
  - Setup

You can use cloud-migration in Azure Cache for Redis to:

- Migrate your apps from your on-premises environment to the cloud.
- Help modernize your current infrastructure as a service (IaaS) apps through the benefits of platform as a service (PaaS) services.

A typical process proceeds as follows:

- From an existing on-premises Redis cache, you export the cache to an RDB file.
- You create an Azure Cache for Redis instance.
- Next, you import the RDB into this instance.
- Finally, you configure your new application to point to your Azure Cache for Redis instance.

![](https://github.com/amarnadh19/books/blob/main/images/az_cache3.png?)


## When to use Azure Cache for Redis

We'll evaluate Azure Cache for Redis against the following criteria:

- Simplicity
- Reliability
- Scaling

### Decision criteria

To determine whether to use Azure Cache for Redis, the following table provides useful criteria.

![](https://github.com/amarnadh19/books/blob/main/images/az_cache4.png?)

### Apply the criteria

#### Do you want a managed service approach?

When you use Azure Cache for Redis, you're implementing a fully managed service. This provides many benefits, including:

- Automatically managed patching, updates, provisioning, configuration, setup, and scaling.
- Implementation of Azure Monitor to track parameters and metrics within the cache, infrastructure, and network.
- Use of any Redis client to connect to the service.

#### Is reliability critical?

Azure Cache for Redis provides several reliability and high-availability features, including clustering, data persistence, zone redundancy, and geo-replication.

Specifically, Azure Cache for Redis has several high-availability capabilities, including that it:

- Includes a redundant pair of VMs configured for automatic failover.

    Note

    This excludes Basic tier.

- Provides up to 99.999% availability in the Enterprise tiers.

- Supports a zone-redundant configuration.

- Supports active geo-replication to create global caches that have local latency across regions.

#### Do you anticipate sudden changes in load?

It's important that the system can respond to changes in load. Sudden changes in demand might occur when you run sales promotions or at specific times of the year. 

Azure Cache for Redis can handle massive throughput and tens of thousands of concurrent users, allowing applications to handle unexpected traffic surges smoothly.