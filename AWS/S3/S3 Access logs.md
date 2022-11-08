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

# S3 Access logs

- For audit purposes, you may want to log all access to S3 buckets
- Any request made to S3, from any account, authorized or denied, will be logged into another [[AWS S3 Bucket]]
- That data can be analyzed using data analysis tools
- Or [[AWS Athena]]

- The log format is at https://docs.aws.amazon.com/AmazonS3/latest/dev/LogFormat.html

![](2019-12-30-13-12-40.png)