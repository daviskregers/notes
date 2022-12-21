---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/vpc, development/networking, review]
sr-due: 2022-11-24
sr-interval: 1
sr-ease: 130
---

- Capture information about IP traffic going into your interfaces
    - [[VPC Flow Logs]]
    - [[Subnet Flow Logs]]
    - [[Elastic network Interface Flow Logs]]
- Helps to [[monitor]] & [[troubleshoot]] [[connectivity issues]]
- Flow logs data can go to [[AWS S3]] / [[CloudWatch Logs]]
- Captures network information from AWS managed interfaces too: [[Elastic Load Balancer]], [[AWS RDS]], [[ElastiCache]], [[Redshift]], [[AWS WorkSpaces]].

## Flow Log Syntax

```
<version> <account-id> <interface-id> <srcaddr> <dstaddr> <srcport> <dstport> <protocol> <packets> <bytes> <start> <end> <action> <log-status>
```
- srcaddr, dstaddr help identify problematic IP
- srcport, dstport help identify problematic ports
- Action: success of failure of the request due to [[Security Group]] / [[Network ACL]]
- Can be used for analytics on usage patterns or malicious behaviour
- Flow logs example [https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html#flow-log-records](https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html#flow-log-records)
- Query VPC flow logs using [[AWS Athena]] on [[AWS S3]] or [[CloudWatch Logs Insights]]

![](2020-01-01-17-51-18.png)

![](2020-01-01-17-52-24.png)

![](2020-01-01-17-53-34.png)

![](2020-01-01-17-54-23.png)

![](2020-01-01-17-55-13.png)

![](2020-01-01-17-59-01.png)

![](2020-01-01-17-59-30.png)

[[VPC Flow Logs + Athena]]