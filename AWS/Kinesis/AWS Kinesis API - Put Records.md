---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/kinesis, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

## AWS Kinesis API - Put records

- PutRecord API + Partition key that gets hashed
- Key is hashed to determine shard id
- The same key goes to the same partition (helps with ordering for a specific key)
- Messages sent get a "sequence number"
- Choose a partition key that is highly distributed (helps prevent "hot partition")
    - user_id if many users
    - Not country_id if 90% of the users are in one country
- Use batching with PutRecords to reduce costs and increase throughput
- ProvisionedThroughPutExceeded if we go over the limits
- Can use CLI, AWS SDK, or producer libraries from various frameworks