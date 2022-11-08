---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/s3, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# S3 Cross region replication

- Must enable [[S3 versioning]] (source and destination)
- Buckets must be in different AWS regions
- Can be in different accounts
- Copying is asynchronous
- Must give proper [[IAM permission]] to [[AWS S3]]
- Use cases
    - Compliance
    - Lower latency access
    - Replication across accounts

![](2019-12-30-13-14-45.png)