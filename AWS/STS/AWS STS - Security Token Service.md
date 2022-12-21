---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/sts, review]
sr-due: 2022-11-28
sr-interval: 1
sr-ease: 190
---

# AWS STS - Security Token Service

- Allows to grant limited and temporary access to AWS resources
- Token is valid for up to one hour (must be refreshed)
- [[Cross Account Access]]
    - Allows users from one AWS account to access resources in another
- [[Identity Federation]] ([[Active Directory]])
    - Provides a non-AWS user with temporary AWS access by linking users [[Active Directory]] credentials
    - Uses [[SAML]] (Security Assertion Markup Language)
    - Allows [[Single Sign On (SSO)]] which enables users to log into [[AWS console]] without assigning IAM credentials
- Federation with third part providers / [[Programming/AWS/Cognito/AWS Cognito]]
    - used mainly in web and mobile applications
    - Makes use of Facebook/Google/Amazon etc to federate them

![[Cross Account Access]]
