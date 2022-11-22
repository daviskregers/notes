---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/s3/tiers, review]
sr-due: 2022-12-16
sr-interval: 24
sr-ease: 250
---

## Amazon S3 One Zone-Infrequent Access

- Same as [[S3 Standard-Infrequent Access (IA) Tier]] but is stored in a single [[Availability Zone]]
- High [[durability]] (99.999999999%) of objects in a single [[Availability Zone]]; data lose when [[Availability Zone]] is destroyed
- 99.95 Availability
- Low latency and high throughput performance
- Supports [[SSL]] for data at transit and [[encryption at rest]]
- Low cost compared to [[S3 Standard-Infrequent Access (IA) Tier]] (by 20%)
- Use cases: storing secondary backup copies of on-premise data, or storing data you can recreate