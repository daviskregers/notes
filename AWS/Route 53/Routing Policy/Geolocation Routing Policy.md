---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-developer-associate-dva-c01/
Tags: [development/aws/route-53/routing-policy, review]
sr-due: 2023-01-17
sr-interval: 56
sr-ease: 270
---

# Route 53 - Routing Policies - Geolocation

- Different from [[Latency based Routing Policy]]!
- This routing is based on user [[location]]
- Specify location by Continent, Country or by US State (if there's overlapping, most precise location is selected)
- Should create a [[Default record]] (in case there's no match on location)
- Use cases: [[website localization]], restrict content distribution, [[load balancing]]..
- Can be associated with [[health checks]]

![](2022-02-08-07-14-17.png)