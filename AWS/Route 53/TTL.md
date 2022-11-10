---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/rds/route-53, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

## TTL

In order not to overload the [[DNS]], we use [[TTL]] to cache the [[DNS]] response for the provided duration. If the [[IP address]] of the server would change not all of the clients would see the change before the [[TTL]] expires.

The TTL can be set when creating records:

![](2019-12-30-10-11-38.png)
