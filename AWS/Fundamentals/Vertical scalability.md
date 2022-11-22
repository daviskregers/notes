---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/fundamentals, review]
sr-due: 2023-01-13
sr-interval: 52
sr-ease: 270
---

## Vertical Scalability

- Vertical scalability means increasing the size of the instance
- For example, your application runs on a t2.micro
- Scaling that application vertically means running it on a t2.large
- Vertical scalability is very common for non distributed systems, such as databases.
- [[AWS RDS]], [[ElastiCache]] are services that can scale vertically.
- There's usually a limit to how much you can vertically scale ([[hardware limit]])