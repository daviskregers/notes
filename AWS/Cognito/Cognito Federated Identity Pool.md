---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/api-gateway, review]
sr-due: 2022-12-15
sr-interval: 23
sr-ease: 250
---

## Cognito Identity Pools (Federated Identity)

- Provide AWS credentials to users so they can access AWS resources directly
- Integrate with [[Cognito User Pool]] as an [[identity provider]]
- Goal
	- Provide direct access to AWS Resources from the Client Side
- How
	- Log in to federated identity provider - or remain anonymous
	- Get temporary AWS credentials back from the Federated Identity Pool
	- These credentials come with a pre-defined [[IAM Policy]] stating their permissions
- Example
	- provide (temporary) access to write to [[AWS S3 Bucket]] using Facebook Login

## For Public Applications

- Goal:
    - Provide direct access to AWS Resources from the Client Side
- How:
    - Log in to federated [[identity provider]] - or remain anonymous
    - Get temporary AWS credentials back from the Federated Identity Pool
    - These credentials come with a pre-defined [[IAM Policy]] stating their permissions
- Example
    - provide (temporary) access to write to S3 bucket using Facebook Login
- Note
    - Web Identity Federation is an alternative to using [[Programming/AWS/Cognito/AWS Cognito]] but AWS recommends against it.

![](2020-01-01-15-20-47.png)

