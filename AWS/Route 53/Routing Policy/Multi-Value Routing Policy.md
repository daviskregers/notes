---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-developer-associate-dva-c01/
Tags: [development/aws/rds/route-53/routing-policy, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# Route 53 - Routing Policies - Multi-Value

- Use when routing traffic to multiple resources
- Route 53 return multiple values/resources
- Can be associated with Health Checks (return only values for healthy resources)
- Up to 8 healthy records are returned for each Multi-Value query
- Multi Value is not a substitute for having an ELB (it's kind of a client side load balancer)

The difference between simple routing policy is that this supports health checks and will return records based on them.