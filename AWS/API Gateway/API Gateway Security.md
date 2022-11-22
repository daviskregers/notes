---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/api-gateway, review]
sr-due: 2022-12-16
sr-interval: 24
sr-ease: 250
---

## Security

- IAM Permissions
    - Create an [[IAM Policy]] authorisation and attach to User / Role
    - [[AWS API Gateway]] verifies [[02-iam-permissions-for-lambda-functions | IAM permissions]] passed by the calling application
    - Good to provide access within your own infrastructure
    - Leverages "[[Sig v4]]" capability where IAM credential are in headers
    - Great for users / roles already within your AWS account
- [[Lambda Authorized]] (formerly Custom Authorisers)
    - Uses [[AWS Lambda]] to validate the token in header being passed
    - Option to cache result of authentication
    - Helps to use [[OAuth]] / [[SAML]] / 3rd party type of authentication
    - Lambda must return an [[IAM Policy]] for the user
    - Pay per Lambda invocation
- [[Programming/AWS/Cognito/AWS Cognito]] User Pools
    - Cognito fully manages [[user lifecycle]]
    - [[AWS API Gateway]] verifies identity automatically from [[Programming/AWS/Cognito/AWS Cognito]]
    - No custom implementation required
    - Cognito only helps with [[authentication]], not [[authorisation]]