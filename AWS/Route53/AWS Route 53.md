---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/rds/route-53, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# AWS Route 53 Overview

- Route53 is a Managed [[DNS (Domain Name System)]]
- DNS is a collection of rules and records which helps clients understand how to reach a server through URLs
- In AWS, the most common records are:
    - [[A RECORD ]]: URL to IPv4
    - [[AAAA RECORD]]: URL to IPv6
    - [[CNAME RECORD]]: URL to URL
    - [[ALIAS RECORD]]: URL to AWS resource

![](2019-12-30-09-56-33.png)

- Route53 can use:
    - public domain names you own (or buy)
    - private domain domain names that can be resolved by your instances in your VPCs
- Route53 has advanced features such as:
    - [[Load Balancing]] (through DNS - also called client load balancing)
    - [[Health Checks]] (although limited)
    - [[Routing Policy]]: simple, failover, geolocation, latency, weighted, multi value

You pay $0.50 per month per hosted zone.

[[Route 53 Hands on]]