---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/types, review]
sr-due: 2023-01-16
sr-interval: 55
sr-ease: 270
---

## Spot instances 

- short workloads, for cheap, can lose instances

- Can get a discount of up to 90% compared to [[EC2 On Demand Instances]]
- You bid a price and get the instance as long as it's price is under the price
- Price varies on offer and demand
- Spot instances are reclaimed with a 2 minute notification warning when the spot price goes above your bid
- Used for [[batch jobs]], [[Big Data analysis]], or workloads that are resilient to failures.
- Not great for [[critical jobs]] or [[databases]].