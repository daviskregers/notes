---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/rds, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

## RDS Read replicas for read scalability

- Up to 5 [[Read Replica]]s
- Within [[Availability Zone]], [[Cross Availability Zone]] or [[Cross Region]]
- Replication is ASYNC, so reads are eventually consistent.
- Applications must update the connection string to leverage read replicas

![](2019-12-30-08-26-23.png)
