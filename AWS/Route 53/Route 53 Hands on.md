---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/rds/route-53, review]
sr-due: 2022-11-25
sr-interval: 3
sr-ease: 230
---

# Route53 hands on

You can navigate to [[AWS Route 53]] via your [[AWS Console]]. 
There we can `Register domain` if you wish to buy a domain, we can also transfer already owned domains.

When opening up hosted zone from a domain, we can setup its [[DNS records]].

![](2019-12-30-10-05-25.png)

## EC2 Setup

We can create an [[AWS EC2]] instances in multiple [[Availability Zone]], create an [[Application Load Balancer (v2)]] for them, then create an alias in the [[AWS Route 53]] to the [[Load Balancer]].

![[TTL]]

![[ CNAME vs ALIAS ]]

[[Simple Routing Policy]]
[[Weighted Routing Policy]]
[[Latency based Routing Policy]]
[[Failover Routing Policy]]
[[Geolocation Routing Policy]]
[[Multi-Value Routing Policy]]
[[Route 53 Health Checks]]

![[ Route 53 as Registrar ]]
