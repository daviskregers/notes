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

# Bastion Hosts

- We can use a [[Bastion Host]] to [[SSH]] into our [[private instance]]s
- The bastion is in the [[public subnet]] which is then connected to all other [[private subnet]]s
- Bastion Host [[security group]] must be tightened

> Tip: Make sure the bastion host port only has 22 traffic from the IP you need, not from the [[security group]]s of your other instances.