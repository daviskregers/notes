---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/kinesis, review]
sr-due: 2022-12-15
sr-interval: 23
sr-ease: 250
---

## Kinesis Streams Shards

- One steam is made of many different shards
- 1MB/s or 1000 messages/s at write PER [[SHARD]]
- 2MB/s at read PER SHARD
- Billing is per shard provisioned, can have as many shards as you want
- Batching available or per message calls
- The number of shards can evolve over time ([[reshard]] / [[merge]])
- Records are ordered per shard