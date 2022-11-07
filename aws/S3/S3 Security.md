---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/s3, development/aws/security, development/security, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# S3 Security

- User based
    - IAM policies - which API calls should be allowed for a specific user from IAM console
- Resource based
    - Bucket policies - bucket wide rules from the s3 console - allows cross account
    - Object Access Control List (ACL) - finer grain
    - Bucket Access Control List (ACL) - less common
- JSON based policies
    - Resources - buckets and objects
    - Actions - set of API to allow or deny
    - Effect - Allow or deny
    - Principal - the account or user to apply the policy to
- Use S3 bucket for policy to:
    - Grant public access to the bucket
    - Force objects to be encrypted at upload
    - Grant access to another account (cross account)

- Other:
    - Networking
        - Supports VPC endpoints (For instances in VPC without www internet)
    - Logging and Audit
        - S3 access logs can be stored in other S3 buckets
        - API calls can be logged in AWS CloudTrail
    - User Security
        - MFA (multi factor authentication) can be required in versioned buckets to delete objects
        - Signed URLS: URLs that are valid only for a limited time (ex premium video service for logged in users)

The permissions can be modified in the permissions tab of the bucket.

![](2019-12-30-12-07-58.png)

When using the `Bucket Policy` tag, we can use [https://awspolicygen.s3.amazonaws.com/policygen.html](https://awspolicygen.s3.amazonaws.com/policygen.html) to generate the json code.