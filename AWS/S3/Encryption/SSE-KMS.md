---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/s3/encryption, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

SSE-KMS
- leverage [[AWS KMS (Key Management Service)]] to mange [[encryption key]]s
- KMS Advantages: user control + audit trail
- Object is encrypted [[server side]]
- Must set header `"x-amz-server-side-encryption": "aws:kms"`