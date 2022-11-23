---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/vpc, networking, review]
sr-due: 2022-11-24
sr-interval: 1
sr-ease: 170
---

# Direct Connect

- Provides a dedicated [[private connection]] from a [[remote network]] to your [[VPC]]
- Dedicated connection must be setup between your DC and [[AWS Direct Connect locations]]
- You need to setup a [[Virtual Private Gateway]] on your [[VPC]]
- Access public resources ([[AWS S3]]) and private ([[AWS EC2]]) on same connection
- Use cases:
    - Increase bandwidth throughput - working with large data sets - lower cost
    - More consistent network experience - applications using real-time data feeds
    - Hybrid environments (on-premises + cloud)
- Supports both [[IPv4]] and [[IPv6]]

![](2020-01-01-18-10-38.png)

![[Direct Connect Gateway]]

