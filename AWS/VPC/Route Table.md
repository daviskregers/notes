---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/vpc, networking, review]
sr-due: 2022-11-24
sr-interval: 1
sr-ease: 130
---

## Editing Route tables

We are going to create a public route table for [[public subnet]]s.

![](2020-01-01-16-32-23.png)

And a private Route Table For [[private subnet]]s.

![](2020-01-01-16-33-07.png)

Then, we want to edit the associations and add public subnets to the public route table, private to private.

![](2020-01-01-16-35-32.png)

Then we are going to edit the routes of the public route table and add [[Internet Gateway]].

![](2020-01-01-16-36-49.png)

![](2020-01-01-16-37-04.png)

Now, we can connect to the [[SSH]].