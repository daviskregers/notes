---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/cognito, saml, identity-federation, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

## What's Identity Federation?

- Federation lets users outside of AWS to assume temporary role for accessing AWS resources.
- These users assume identity provided access role.
- Federation assumes a form of 3rd part authentication:
    - [[LDAP]]
    - Microsoft [[Active Directory]] (~=[[SAML]])
    - [[Single Sign On]]
    - [[Open ID]]
    - [[Programming/AWS/Cognito/AWS Cognito]]
- Using federation, you don't need to create [[IAM]] users (user management is outside of AWS)

![](2020-01-01-15-15-36.png)