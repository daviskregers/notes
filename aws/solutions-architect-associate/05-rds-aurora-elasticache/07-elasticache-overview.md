# ElastiCache overview

- The same way RDS is to get managed Relational Databases
- ElastiCache is to get managed Redis or Memcached
- Caches are in-memory databases with really high performance, low latency
- Helps reduce load off of databases for read intensive workloads
- Helps make your application stateless
- Write Scaling using sharding
- Read Scaling using Read Replicas
- Multi AZ with Failover Capability
- AWS takes care of OS maintenance / patching, optimizations, setup, configuration, mnonitoring, failure recovery and backups

## Redis Overview

- Redis is an in-memory key-value store
- Super low latency (sub ms)
- Cache survive reboots by default (it's called persitance)
- Great to host
    - User sessions
    - Leaderboard (for gaming)
    - Distributed states
    - Relieve pressure on databases (such as RDS)
    - Pub / Sub capability for messaging
- Multi AZ with Automatic Failover for disaster recovery if you don't want to lose your cache data
- Support for Read Replicas

## Memcached overview

- Memcached is an in-memory object store
- Cache doesn't survive reboots
- Use cases
    - Quick retrieval of objects from memory
    - Cache often accessed objects
- Overall, Redis has largely grown in popularity and has better feature sets than Memcached

## ElastiCache for Solutions Architects

- Security
    - Redis support Redis AUTH (username / password)
    - SSL in-flight encryption must be enabled and used
    - Memcached supports SASL authentication (advanced)
    - None of the caches support IAM authentication
    - IAM policies on ElastiCache are only used for AWS API-level security
- Patterms for ElastiCache
    - Lazy Loading: all the read data is cached, data can become stale in cache
    - Write through: adds or updates data in the cache when writted to a DB (no stale data)
    - Session Store: store temporary session data in a cache (using TTL features)