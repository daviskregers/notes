---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/s3, review]
sr-due: 2023-01-12
sr-interval: 51
sr-ease: 270
---

# S3 Pre-signed URLs

- Can generate pre-signed [[URL]]s using [[AWS SDK]] or [[AWS CLI]]
    - For downloads (easy, can use the [[AWS CLI]])
    - For uploads (harder, must use the [[AWS SDK]])
- Valid for a default of 3600 seconds, can change timeout with `--expires-in` argument
- Users given a pre-signed URL inherit the permissions of the person who generated the [[URL]] for [[HTTP GET]]/[[HTTP PUT]]

- Examples
    - Allow only logged-in users to download a premium video on your [[AWS S3 Bucket]]
    - Allow an ever changing list of users to download files by generating [[URL]]s dynamically
    - Allow temporarily a user to upload file to a precise location in your bucket

```
aws s3 presign s3://my-sample-bucket-monitored/file.txt --expires-in 300 --region eu-west-1
```