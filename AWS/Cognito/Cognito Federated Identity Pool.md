---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/api-gateway, review]
sr-due: 2022-11-10
sr-interval: 3
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