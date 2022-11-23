---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/vpc, networking, review]
sr-due: 2022-11-27
sr-interval: 4
sr-ease: 210
---

# VPC endpoint

![](2020-01-01-17-37-36.png)

- Endpoints allow you to connect to AWS Services using a [[private network]] instead of the [[public network]].
- They scale horizontally and are [[redundant]]
- They remove the need of [[Internet Gateway & Route tables]], [[NAT]], etc to access AWS Services
- Interface: provisions an [[ENI]] (private IP address) as an entry point (must attach [[Security Group]]) - most AWS service.
- [[Gateway]]: provisions a target and must be used in a [[Route Table]] - [[AWS S3]] and [[DynamoDB]]
- In case of issues:
    - Check [[DNS Setting Resolution]] in your [[VPC]]
    - Check [[Internet Gateway & Route tables]]

![](2020-01-01-17-43-40.png)
![](2020-01-01-17-43-58.png)

Now the [[Private Subnet]] should have access to [[AWS S3]] without any internet access (if we remove that [[Internet Gateway & Route tables]]), provided the [[AWS EC2]] instance has the correct [[IAM]] permissions.

![](2020-01-01-17-44-32.png)