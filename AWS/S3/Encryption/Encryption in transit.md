---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/s3/encryption, review]
sr-due: 2023-01-12
sr-interval: 51
sr-ease: 270
---

## Encryption in transit (SSL)

- [[AWS S3]] exposes
    - [[HTTP endpoint]]: not encrypted
    - [[HTTPS endpoint]]: [[encryption in flight]]

- You're free to use the [[endpoint]] you want, but [[HTTPS]] is recommended
- [[HTTPS]] is mandatory for [[SSE-C]]
- Encryption in flight is also called [[SSL - TLS]]

![](2019-12-30-11-59-39.png)

![](2019-12-30-12-00-13.png)