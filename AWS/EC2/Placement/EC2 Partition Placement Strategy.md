---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/placement, review]
sr-due: 2022-12-16
sr-interval: 24
sr-ease: 250
---

## Partition Placement Strategy

![](../../../images/2019-11-22-13-32-47.png)

- Up to 7 partitions per [[Availability Zone]]
- Up to 100s of [[AWS EC2]] instances
- The instances in a partition do not share racks with the instances in other partitions

- A [[partition failure]] can affect many [[AWS EC2]] but won't affect other partitions
- [[AWS EC2]] instances get access to the partition information as metadata

Use cases:
- [[HDFS]]
- [[HBase]]
- [[Cassandra]]
- [[Kafka]]