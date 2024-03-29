---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/architecture, review]
sr-due: 2022-11-25
sr-interval: 3
sr-ease: 230
---

# Stateless Web App: WhatIsTheTime.com

- WhatIsTheTime.com allows people to know what time it is
- We don't need a [[database]]
- We want to start small and can accept [[downtime]]
- We want to full [[Vertical scalability]] and [[Horizontal scalability]], no [[downtime]]
- Let's go through the Solutions Architect journey for this app

## Starting simple

- Create a single t2.micro instance

## Scaling vertically 

- When we have more traffic for the t2.micro instance to handle, we scale it vertically to something like m5.large.
- [[Downtime]] while upgrading to new instance.

## Scaling horizontally

- Instead of scaling vertically, we can add multiple instances to balance the load between them.
- In one instance goes away, we can leverage [[Load Balancer]] and [[Health Checks]] to route clients to a different instance.
- We can use [[Auto Scaling Group (ASG)]] to manage the instance count automatically
- In order to make our app disaster tolerant, we can also make it [[Multi AZ]].