---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/architecture, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# Software updates offloading

- We have an application running on [[AWS EC2]] that distributes software updates once in a while
- When a new software update is out, we get a lot of requests and the content is distributed in mass over the network. It's very costly
- We don't want to change our application, but want to optimise our cost and [[CPU]], how can we do it?

Current state:

![](2020-01-01-12-32-11.png)

Easy fix:

![](2020-01-01-12-32-43.png)

## Why [[Programming/AWS/CloudFront/AWS CloudFront]]?

- No changes in architecture
- Will [[cache]] software update files at the [[edge]]
- Software update files are not dynamic, they're static (never changing)
- Our [[AWS EC2]] instances aren't [[serverless]]
- But [[Programming/AWS/CloudFront/AWS CloudFront]] is, and will scale for us
- Our [[Auto Scaling Group (ASG)]] will not scale as much, and we'll save tremendously in [[AWS EC2]]
- We'll also save in availability, network bandwith cost etc

