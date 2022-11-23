---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ecs, development/aws/ec2/elastic-loadbalancer, review]
sr-due: 2022-11-24
sr-interval: 1
sr-ease: 130
---

## AWS ECS - ALB Integration

- [[Application Load Balancer (v2)]] has a direct integration feature with [[ECS - Elastic Container Service]] called "[[port mapping]]"
- This allows you to run multiple instances of the same application on the same [[AWS EC2]] machine
- Use cases
    - Increased [[resiliency]] even if running on one [[AWS EC2]] instance
    - Maximise [[utilisation]] of [[CPU]] / cores
    - Ability to perform [[rolling upgrade]]s without impacting [[application uptime]]

![](2020-01-02-14-47-29.png)
