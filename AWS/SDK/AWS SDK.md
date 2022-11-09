---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/sdk, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# AWS SDK Overview

- What if you want to perform actions on AWS directly from your applications code? (Without using the [[AWS CLI]]).
- You can use [[SDK]] (Software development kit)
- Official SDKs are:
    - [[Java]]
    - [[.NET]]
    - [[Node.js]]
    - [[PHP]]
    - [[Python]] (named boto3 / botocore)
    - [[Go]]
    - [[Ruby]]
    - [[C++]]
- We have to use the AWS SDK when coding against AWS Services such as [[Programming/AWS/solutions-architect-associate/14-databases-in-aws/DynamoDB]]
- The [[AWS CLI]]I uses the Python SDK (boto3)
- Good to know: if you don't specify or configure a default [[AWS Region]], then us-east-1 will be chosen by default.

- It's recommended to use the default credential provider chain
- The default credential provider chain works seamlessly with:
    - AWS credentials at `~/.aws/credentials/` (only on our computers or on premise)
    - Instance Profile Credentials using [[IAM Role]]s (fro [[AWS EC2]] machines, etc)
    - [[Environment variables]] (AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY)
- Overall, never store aws credentials in your code.
- Best practice is for credetnials to be inherited from mechanisms above and 100% [[IAM Role]]s if working from within AWS services.