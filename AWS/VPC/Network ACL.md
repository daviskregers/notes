---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/vpc, networking, review]
sr-due: 2022-11-24
sr-interval: 1
sr-ease: 130
---

# Network ACLs & Security Groups

## Network ACLs

- [[NACL]] are like a [[firewall]] which control traffic from and to [[subnet]]
- [[Default NACL]] allows everything outbound and everything inbound
- One NACL per [[Subnet]], new Subnets are assigned to the Default NACL
- Define NACL rules
    - Rules have a number(1-32766) and higher precedence with a lower number
    - If you define #100 ALLOW <IP> and #200 DENY <IP> , [[IP]] will be allowed
    - Last rule is an asterisk (*) and denies a request in case of no rule match
    - AWS recommends adding rules by increment of 100
- Newly created NACL will deny everything
- NACL are a great way of blocking a specific IP at the subnet level

https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html

## Incoming Request

![](2020-01-01-17-20-39.png)

## Outgoing Request

![](2020-01-01-17-21-05.png)

---

If we look at our DemoVPC NACL, we can see that all the inbound traffic is allowed, as well as all [[outbound network]].

![](2020-01-01-17-22-49.png)

![](2020-01-01-17-22-59.png)

## Network ACLs vs Security Groups

![](2020-01-01-17-24-40.png)

https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Security.html#VPC_Security_Comparison