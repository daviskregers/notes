---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# Security Groups Deep Dive

- Security Groups are acting as a `firewall` on EC2 instances.
- They regulate
    - Access to Ports
    - Authorised IP ranges - IPv4 and IPv6
    - Control of inbound network (from other to the instance)
    - Control of outbound network (from the instance to other)

    ![](../../../images/2019-11-22-11-38-11.png)

    ![](../../../images/2019-11-22-11-39-26.png)

- Can be attached to multiple instances
- Locked down to a region / VPC combination
- Does live "outside" the EC2 - if traffic is blocked the EC2 instance won't see it.
- It's a good to maintain one separate security group for ssh access
- If your application is not accessable (timeout) then it's a security group issue
- If your application gives a "connection refused"'error, then it's an application error or it's not launched
- All inbound traffic is blocked by default
- All outbound is authorised by default

## Referencing other security groups

When we have multiple instances on the same security groups, they can communicate.

![](../../../images/2019-11-22-11-43-09.png)