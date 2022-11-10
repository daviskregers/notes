---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/dynamodb, cache, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

- Seamless cache for [[DynamoDB]], no application re-write
- Writes go though DAX to DynamoDB
- Micro second latency for cached reads & queries
- Solves the [[Hot Key problem]] (too many reads)
- 5 minutes [[TTL]] for cache by default
- Up to 10 nodes in the cluster
- Multi AZ (3 nodes minimum recommended for production)
- Secure (Encryption at rest with [[AWS KMS (Key Management Service)]], [[VPC]], [[IAM]], [[CloudTrail]])