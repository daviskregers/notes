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

# VPC Peering

- Connect two [[VPC]], privately using AWS' network
- Make them behave as if they were in the same network
- Must not have overlapping [[CIDR]]
- [[VPC Peering connection]] is not transitive (must be established for each [[VPC]] that need to communicate with one another)
- You must update [[Route Table]] in each [[VPC]]'s [[Subnet]]s to ensure instances can communicate

![](2020-01-01-17-30-58.png)

![](2020-01-01-17-31-27.png)

--- 

We can create a peering connection to connect our [[Default VPC]] with our DemoVPC.

![](2020-01-01-17-33-22.png)

![](2020-01-01-17-33-55.png)

Now we have to update the PublicRouteTable and DefaultRouteTable

![](2020-01-01-17-36-03.png)

![](2020-01-01-17-36-39.png)