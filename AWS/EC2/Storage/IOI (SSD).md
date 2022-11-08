---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/storage/ebs, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

IOI (SSD): Highest performance SSD volume for mission-critical low-latency or high throughput workloads

- Critical business applications that require sustained IOPS performance, or more than 16000 IOPS per volume (gp2 limit)
- Large database workloads such as
	- MongoDB, Cassandra, Microsoft SQL Server, MySQL, PostgreSQL, Oracle
- 4 GiB - 16TiB
- IOPS is provisioned ([[PIOPS]]) - Min 100 - Max 64'000 ([[Nitro instances]]) else MAX 32'000 (other instances)
- The maximum ratio of provisioned IOPS to requested volume size (in GiB) is 50:1. (For each GiB we can request 50 [[IOPS]]).