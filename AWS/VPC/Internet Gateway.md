---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/vpc, development/networking, review]
sr-due: 2022-12-05
sr-interval: 8
sr-ease: 150
---

## Internet Gateway

- Internet Gateways help our VPC instances connect with the internet
- It scales horizontally and is [[Highly Available]] and [[redundant]]
- Must be created separately from [[VPC]]
- One [[VPC]] can only have attached to one [[Internet Gateway]] and vice versa
- Internet Gateway is also a [[NAT]] for the instances that have a [[public IPv4]]
- internet gateways on their own do not allow [[internet access]]
- [[Route Table]]s must also be edited

## Creating an Internet Gateway

![](2020-01-01-16-29-41.png)

It will show as detached

![](2020-01-01-16-30-12.png)

![](2020-01-01-16-30-24.png)

![](2020-01-01-16-30-43.png)

![](2020-01-01-16-31-08.png)

Now if we would try to [[ssh]], it still wouldn't work, because we have to edit the [[Route Table]].