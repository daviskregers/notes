---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/iam, review]
sr-due: 2022-12-11
sr-interval: 20
sr-ease: 250
---

Best practices

- One [[IAM]] User per physical person
- One [[IAM Role]] per application
- IAM credentials should never be shared
- Never write IAM credentials in code
- Never use the root account except for initial setup
- Never use the root IAM credentials

- Assign users to groups and assign permissions to groups
- Create a strong password policy
- Use and enforce the use of Multi Factor Authentication (MFA)
- Create and use Roles for giving permissions to AWS services
- Use Access Keys for Programmatic Access (CLI/SDK)
- Audit permissions of your account with the IAM Credentials Report
- **Never share IAM users & access keys**