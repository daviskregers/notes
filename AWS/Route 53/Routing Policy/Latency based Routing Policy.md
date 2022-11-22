---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-developer-associate-dva-c01/
Tags: [development/aws/route-53/routing-policy, review]
sr-due: 2023-01-10
sr-interval: 49
sr-ease: 270
---

# Route 53 - Routing Policies - Latency based

- Redirect to the resource that has the least [[latency]] close to us
- Super helpful when [[latency]] for users is a priority
- Latency is based on traffic between users and [[AWS Region]]s
- Germany users may be directed to the US (if that's the lowest latency)
- Can be associated with Health Checks (has a failover capability)

![](2022-02-08-06-51-32.png)