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

# NAT Gateway

- AWS Managed [[NAT]], higher bandwidth, better availability, no admin
- Pay by the hour for usage and bandwidth
- [[NAT]] is created in a specific [[Availability Zone]], uses an [[Elastic IP]]
- Cannot be used by an instance in that subnet (only from other subnets)
- Requires [[Internet Gateway & Route tables]] ([[Private Subnet]] => [[NAT Gateway]] => [[Internet Gateway & Route tables]])
- 5 Gbps of bandwidth with automatic scaling up to 45 Gbps
- No [[security group]] to manage / required

The difference between [[NAT Gateway]] and [[NAT Instance]] can be found here [https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-comparison.html](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-comparison.html)

![](2020-01-01-16-59-01.png)

We are going to create a new NAT Gateway on `PublicSubnetA`

![](2020-01-01-17-01-31.png)

Then we are going to edit the route table of the `PrivateRouteTable`

![](2020-01-01-17-02-35.png)

![](2020-01-01-17-02-50.png)