---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/kms, review]
sr-due: 2022-12-02
sr-interval: 15
sr-ease: 250
---

# AWS KMS (Key Management Service)

- Anytime you hear "[[encryption]]" for an AWS service, it's most likely KMS
- Easy way to [[control access]] to your data, AWS manages keys for us
- Fully integrated with [[IAM]] for authorisation
- Seamlessly integrated into:
    - [[EBS Volume]]: encrypt volumes
    - [[AWS S3]]: Server side encryption of objects
    - [[Redshift]]: encryption of data
    - [[AWS RDS]]: encryption of data
    - [[SSM Parameter Store]]: Parameter store
    - etc
- But you can also use the [[AWS CLI]] / [[AWS SDK]]

- Able to fully manage the keys & policies
    - Create
    - Rotation policies
    - Disable
    - Enable
- Able to audit key usage (using [[CloudTrail]])
- Three types of Customer Master Keys ([[CMK]])
    - AWS Managed Service Default CMK: free
    - User Keys created in KMS: $1 / month
    - User Keys imported (must be 256-bit [[symmetric key]]): $1/month
- + pay for API call to KMS ($0.03/ 10000 calls)

![[ KMS 101]]

![[KMS API]]

![[ Encryption in AWS Services]]
