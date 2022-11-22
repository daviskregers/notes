---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/elastic-loadbalancer, review]
sr-due: 2022-12-18
sr-interval: 26
sr-ease: 250
---

## Network Load Balancer (v2)

- Network [[Load Balancer]]s ([[layer 4]]) allow to do:
    - Forward [[TCP]] traffic to your instances
    - Handle millions of requests per seconds
    - Support for [[static IP]] or [[elastic IP]]
    - Less latency ~100ms (vs 400ms for [[Application Load Balancer (v2)]])
- Network Load Balancers are mostly used for extreme performance and should not be the the default load balancer you choose
- Overall, the creation process is the same as [[Application Load Balancer (v2)]]

![](../../../images/2019-11-22-14-16-45.png)

