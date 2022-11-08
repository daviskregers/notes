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

## AWS Kinesis API - Exceptions

- ProvisionedThroughputExceeded Exceptions
    - Happens when sending more data (exceeding MB/s or TPS for any shard)
    - Make sure you don't have a hot shard (such as your partition key is bad and too much data goes to that partition)
- Solution:
    - Retries with backoff
    - Increase shards (scaling)
    - Ensure your partition key is a good one