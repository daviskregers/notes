---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/s3, review]
sr-due: 2022-12-18
sr-interval: 26
sr-ease: 250
---

# S3 MFA Delete

- [[Multi factor authentication]] forces user to generate a code on a device (usually mobile phone or hardware) before doing important operations on S3
- To use MFA-Delete, enable [[S3 Versioning]] on the [[AWS S3 Bucket]]
- You will need [[Multi factor authentication]] to
    - Permanently delete an [[S3 Object Version]]
    - Suspend version on the bucket
- You won't need [[Multi factor authentication]] for
    - Enabling [[S3 Versioning]]
    - Listing deleted versions

- Only the bucket owner ([[AWS Root Account]]) can enable/disable MFA-delete
- MFA-Delete currently can only be enabled using the CLI

```
aws s3api put-bucket-versioning --bucket mfa-demo --versioning-configuration Status=Enabled,MFADelete=Enabled --mfa "arn-of-mfa-device mfa-code" --profile root-datacumulus
```

The code can be gotten from `IAM` when [[Multi factor authentication]] is set up.