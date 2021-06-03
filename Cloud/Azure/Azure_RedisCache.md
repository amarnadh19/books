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


