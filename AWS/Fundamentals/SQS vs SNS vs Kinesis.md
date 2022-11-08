---
Created: 2022-11-08 08:37:32
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/fundamentals]
---

# SQS vs SNS vs Kinesis

## [[AWS SQS]]

- Consumer "pulls data"
- Data is deleted after being consumed
- Can have as many workers (consumers) as we want
- No need to provision throughput
- No ordering guarantee (except FIFO queues)
- Individual message delay capability

## [[AWS SNS]]

- Push data to many subscribers
- Up to 10,000,000 subscribers
- Data is not persisted (list if not delivered)
- [[Pub-Sub]]
- Up to 100,000 topics
- No need to provision throughput
- Integrates with [[AWS SQS]] for fanout architecture pattern

## [[Kinesis]]

- Consumers pull data
- As many consumers as we want
- Possibility to replay data
- Meant for real-time big data analytics and [[ETL]]
- Ordering at the shard level
- Data expires after X days
- Must provision throughput