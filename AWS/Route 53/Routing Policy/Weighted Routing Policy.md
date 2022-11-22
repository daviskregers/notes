---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-developer-associate-dva-c01/
Tags: [development/aws/route-53/routing-policy, review]
sr-due: 2022-12-16
sr-interval: 24
sr-ease: 250
---

# [[AWS Route 53]] - Routing Policies - Weighted

- Control the % of the requests that go to each specific resource
- Assign each record a relative weight:
    - traffic (%) = (weight for a specific record) / (sum of all weights)
    - Weights don't need to sum up to 100
- [[DNS records]] must have the same name and type
- Can be associated with [[health checks]]
- Use cases: [[load balancing]] between regions, testing new application versions...
- Assign a weight of 0 to a record to stop sending traffic to that resource
- If all records have weight of 0 then all records will be returned equally

![](2022-02-08-06-48-20.png)