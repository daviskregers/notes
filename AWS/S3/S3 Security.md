---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/s3, development/aws/security, development/security, review]
sr-due: 2022-12-14
sr-interval: 22
sr-ease: 250
---

# S3 Security

- User based
    - [[IAM Policy]] - which API calls should be allowed for a specific user from IAM console
- Resource based
    - [[bucket policy]] - bucket wide rules from the s3 console - allows cross account
    - [[Object Access Control List (ACL)]] - finer grain
    - [[Bucket Access Control List (ACL)]] - less common
- [[JSON]] based policies
    - Resources - buckets and objects
    - Actions - set of API to allow or deny
    - Effect - Allow or deny
    - Principal - the account or user to apply the policy to
- Use [[AWS S3 Bucket]] for policy to:
    - Grant public access to the bucket
    - Force objects to be encrypted at upload
    - Grant access to another account (cross account)

- Other:
    - [[Networking]]
        - Supports [[VPC endpoint]] (For instances in VPC without www internet)
    - [[Logging]] and [[Audit]]
        - [[S3 access logs]] can be stored in other S3 buckets
        - [[API]] calls can be logged in [[AWS CloudTrail]]
    - [[User Security]]
        - [[Multi factor authentication]] can be required in [[S3 Versioning|versioned]] [[AWS S3 Bucket]] to delete [[AWS S3 Objects]]
        - [[S3 Pre-signed URLs]]: [[URL]]s that are valid only for a limited time (ex premium video service for logged in users)

The permissions can be modified in the permissions tab of the [[AWS S3 Bucket]].

![](2019-12-30-12-07-58.png)

When using the `Bucket Policy` tag, we can use [https://awspolicygen.s3.amazonaws.com/policygen.html](https://awspolicygen.s3.amazonaws.com/policygen.html) to generate the [[JSON]] code.