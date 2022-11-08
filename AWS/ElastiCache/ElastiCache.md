---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/elasticache, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# ElastiCache overview

- The same way [[AWS RDS]] is to get managed Relational Databases
- ElastiCache is to get managed [[Redis]] or [[Memcached]]
- Caches are in-memory databases with really high performance, low latency
- Helps reduce load off of databases for read intensive workloads
- Helps make your application stateless
- Write Scaling using [[sharding]]
- Read Scaling using [[Read Replica]]s
- Multi AZ with Failover Capability
- AWS takes care of [[OS maintenance]] / [[patching]], optimizations, setup, configuration, monitoring, [[failure recovery]] and [[backups]]

![[Redis]]

![[Memcached]]

## ElastiCache for Solutions Architects

- Security
    - [[Redis]] support [[Redis AUTH]] (username / password)
    - SSL [[in-flight encryption]] must be enabled and used
    - [[Memcached]] supports [[SASL authentication]] (advanced)
    - None of the caches support IAM authentication
    - IAM policies on ElastiCache are only used for AWS API-level security

- Patterns for ElastiCache

![[Lazy Loading Pattern]]

![[Write through Pattern]]

![[Session Store Pattern]]