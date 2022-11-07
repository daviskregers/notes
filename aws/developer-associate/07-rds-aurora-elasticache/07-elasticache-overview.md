# Amazon ElastiCache Overview

- The same way RDS is to get managed Relational Databases the ElastiCache is to get a manged Redis or Memcached
- Caches are in-memory databases with really high performance, low latency
- Helps reduce load off of databases for read intensive workloads
- Helps make your application stateless
- AWS takes care of OS maintenence / patching, optimizations, setup, configuration, monitoring, failure recovery and backups.

Using ElastiCache involves heavy application code changes.

## ElastiCache Solition Architecture - DB Cache

- Application queries ElastiCache, if not available, get from RDS and store in ElastiCache
- Helps relieve load in RDS
- Cache must have an invalidation strategy to make sure only the most current data is used in there.

![](2021-10-18-09-20-13.png)

## ElastiCache Solution Architecture - User Session Store

- User logs into any of the application
- The application writes the session data into ElastiCache
- The user hits another instance of our application
- The instance retrieves the data and the user is already logged in.

![](2021-10-18-09-21-39.png)

## ElastiCache - Redis vs Memcached

- Redis
    - Multi AZ with Auto-Failover
    - Read replicas to scale reads and have high availability
    - Data Durability using AOF persistence
    - Backup and restore features

- Memcached
    - Multi-node for partitioning of data (sharding)
    - No high availability (replication)
    - Non persistent
    - No backup and restore
    - Multi-threaded architecture