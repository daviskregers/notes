---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/kinesis, review]
sr-due: 2022-12-18
sr-interval: 26
sr-ease: 250
---

## AWS Kinesis API - Consumers

- Can use a normal consumer (CLI, [[AWS SDK]], etc)
- Can use Kinesis Client library (in [[Java]], [[Node]], [[Python]], [[Ruby]], [[.Net]])
    - KCL uses [[DynamoDB]] to checkpoint offsets
    - KCL uses [[DynamoDB]] to track other workers and share the work amongst shards
