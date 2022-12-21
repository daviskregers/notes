---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/vpc, development/networking, review]
sr-due: 2022-11-28
sr-interval: 1
sr-ease: 130
---

# Internet Gateways & Route tables

If we want to create an [[AWS EC2]] instance in the [[subnet]] with a [[public IP]] address, we need to modify the [[public subnet]] to [[auto-assign IP]]s.

![](2020-01-01-16-21-21.png)

![](2020-01-01-16-21-37.png)

![](2020-01-01-16-22-39.png)

When created, we can see that we have a [[private IP]] of `10.0.0.250` and a [[public IP]] of `54.246.162.86`.

![](2020-01-01-16-26-33.png)

Now, even though our [[security group]] allows this, if we were to try to connect to it via [[ssh]], the connection would time out.

This is because the subnet does not have an [[Internet Gateway & Route tables]].

![[Internet Gateway]]

![[Route Table]]
