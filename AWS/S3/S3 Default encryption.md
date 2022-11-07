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

# S3 Default encryption

- The old way to enable default encryption was to use a bucket policy and refuse any HTTP command without the proper headers.
- The new way is to use the "default encryption" option in S3
- Note: Bucket policies are evaluated before "default ecnryption"
