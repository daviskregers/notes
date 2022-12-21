---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/vpc, development/networking, review]
sr-due: 2022-11-30
sr-interval: 7
sr-ease: 230
---

- [[CIDR]] - [[IP Range]]
- [[VPC Summary]] - [[VPC]] => We define a list of [[IPv4]] & [[IPv6]] [[CIDR]]
- [[Subnet]]s - tied to an [[Availability Zone]], we define a [[CIDR]]
- [[Internet Gateway & Route tables]] - at the [[VPC Summary]] level provide [[IPv4]] & [[IPv6]] internet access
- [[Route Table]]s - must be edited to add routes from [[Subnet]]s to the [[Internet Gateway & Route tables]]s, [[VPC peering connection]]s, [[VPC endpoint]]s etc
- [[NAT Instance]]s - gives internet access to instances in [[private subnet]]s. Old, must be setup in a [[public subnet]], disable Source / Destination check flag.
- [[NAT Gateway]] - managed by AWS, provides [[scalable internet access]] to private instances, [[IPv4]] only
- [[Private DNS]] + [[AWS Route 53]] - enable [[DNS resolution]] + [[DNS hostname]]s ([[VPC]])
- [[Network ACL]] - [[stateless]], [[subnet rules]] for inbound and outbound, don't forget [[ephemeral port]]s
- [[Security Group]]s: [[stateful]], operate at the [[AWS EC2]] instance level
- [[VPC Peering]]: Connect two [[VPC]] with non overlapping [[CIDR]] non transitive
- [[VPC endpoint]]s: Provide private access to AWS Services ([[AWS S3]], [[DynamoDB]], [[CloudFormation]], [[SSM Parameter Store]]) within [[VPC]]
- [[VPC Flow Logs]]: Can be setup at the [[VPC]] / [[Subnet]] / [[ENI]] Level for ACCEPT and REJECT traffic, helps identifying attacks, analyse using [[AWS Athena]] or [[CloudWatch Logs Insights]]
- [[Bastion Host]]: Public instance to [[ssh]] into, that has SSH connectivity to instances in [[private subnet]]s
- [[Site to Site VPN]]: Setup a [[Customer Gateway]] on DC, a [[Virtual Private Gateway]] on [[VPC]], and site-to-site VPN over [[public internet]]
- [[Direct Connect]]: Setup a [[Virtual Private Gateway]] on [[VPC]], and establish a [[direct private connection]] to an [[AWS Direct Connect Location]]
- [[Direct Connect Gateway]]: setup a [[Direct Connect]] to many [[VPC]] in different [[AWS Region]]
- [[Egress Only Internet Gateway]]: like a [[NAT Gateway]], but for [[IPv6]]