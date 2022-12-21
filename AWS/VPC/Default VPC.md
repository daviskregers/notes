---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/vpc, development/networking, review]
sr-due: 2022-11-24
sr-interval: 1
sr-ease: 150
---

# Default VPC overview

- All new accounts have a [[Default VPC]]
- New instances are launched into [[Default VPC]] is no [[Subnet]] is specified
- [[Default VPC]] have [[internet connectivity]] and all instances have [[public IP]]
- We also get a public and a private [[DNS name]]

![](2020-01-01-15-49-19.png)

Our account has one default VPC, available hosts - 65536.

![](2020-01-01-15-50-23.png)

Has 3 subnets - 3 availability zones, each has 4091 available [[IP]]s.

![](2020-01-01-15-51-37.png)

We have a [[VPC route table]], which defines that one of the IPs has an [[Internet Gateway & Route tables]]

![](2020-01-01-15-54-01.png)

and has associations to our 3 availability zone subnets

![](2020-01-01-15-54-34.png)

Then our 3 [[Availability Zone]]s allow all [[inbound traffic]] and all [[outbound traffic]] (through [[Network ACL]]):

![](2020-01-01-15-55-44.png)

![](2020-01-01-15-55-55.png)