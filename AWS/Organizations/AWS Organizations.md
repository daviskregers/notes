---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/organizations, review]
sr-due: 2022-12-06
sr-interval: 9
sr-ease: 150
---

# AWS Organizations

- Global service
- Allows to manage multiple [[AWS account]]s
- The main account is the master account - you can't change it
- Other accounts are member accounts
- Member accounts can only be part of one organization
- Consolidated Billing across all accounts - single payment method
- Pricing benefits from aggregated usage (volume discount for [[AWS EC2]], [[AWS S3]]...)
- API is available to automate AWS account creation

## OU & Service Control Policies (SCPs)

- Organise accounts in [[Organizational Unit]] (OU)
    - Can be anything: dev / test / prod or Finance / HR / IT
    - Can nest OU within OU
- Apply [[Service Control Policies]] (SCPs) to OU
    - Permit / Deny access to AWS services
    - SCP has a similar syntax to [[IAM]]
    - It's a filter to [[IAM]]
- Help sandbox account creation
- Help to separate dev and prod resources
- Helpful to only allow approved services
