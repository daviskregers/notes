---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/placement, review]
sr-due: 2022-12-14
sr-interval: 22
sr-ease: 250
---

## Spread Placement Strategy

![](../../../images/2019-11-22-13-30-39.png)

Pros:
- Can span across [[Availability Zone]]s
- Reduced risk of simultaneous failure
- EC2 Instances are on different physical hardware

Cons:
- Limited to 7 instances per [[Availability Zone]] per [[EC2 Placement Groups]]

Use case:
- Application that needs to maximise [[High Availability]]
- [[Critical Applications]] where each instance must be isolated from failure from each other
