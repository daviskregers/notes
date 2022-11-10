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

# Route 53 - Routing Policies

- Define how Route 53 responds to DNS queries
- Don t get confused by the word "Routing"
    - It's not the same as Load Balancer routing which routes the traffic
    - DNS does not route any traffic, it only responds to DNS queries
- Route 53 supporrts the following routing policies
    - Simple
    - Weighted
    - Failover
    - Latency based
    - Geolocation
    - Multi-Value Answer
    - Geoproximity (using ROute 53 Traffic Flow feature)

## Simple Routing Policy

- Typically, route traffic to a single resource
- Can specify multiple values in the same record
- If multiple values are returned, a random one is chosen by the client
- When Alias is enabled, specify only one AWS resource
- Can't be associated with health checks