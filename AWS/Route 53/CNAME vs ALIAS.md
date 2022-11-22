---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/rds/route-53, review]
sr-due: 2023-01-15
sr-interval: 54
sr-ease: 270
---

## CNAME vs ALIAS

AWS Resources ([[Load Balancer]], [[Programming/AWS/CloudFront/AWS CloudFront]] etc) expose an [[AWS URL]] (lb1-1234.us-east-2.elb.amazonaws.com) and you want it to be myapp.mydomain.com
- [[CNAME]]:
    - Points a URL to any other URL. (app.mydomain.com => xyz.anything.com)
- [[Alias]]
    - Points a URL to AWS resource (app.mydomain.com => xyz.amazonaws.com)
    - Works for root domain and non-root domain
    - Free of charge
    - native [[health checks]]

So, for subdomains we can create both [[CNAME]] and [[ALIAS]] for our [[load balancer]], but alias would be the recommended way to go. For root domain, we can only use ALIAS.

![](2019-12-30-10-16-01.png)
