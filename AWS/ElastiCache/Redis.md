---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/elasticache, database, review]
sr-due: 2023-01-16
sr-interval: 55
sr-ease: 270
---

## Redis

- Redis is an [[in-memory]] [[key-value store]]
- Super low latency (sub ms)
- [[Cache]] survive reboots by default (it's called [[persitance]])
- Great to host
    - User sessions
    - Leaderboard (for gaming)
    - Distributed states
    - Relieve pressure on databases (such as RDS)
    - Pub / Sub capability for messaging
- Multi AZ with Automatic Failover for disaster recovery if you don't want to lose your cache data
- Support for Read Replicas