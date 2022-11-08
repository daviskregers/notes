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

## Route 53 Health Checks

- If we have X health checks failed, we mark resource as unhealthy (default 3)
- After X health checks passed, mark as healthy (default 3)
- Default Health Check interval: 30 seconds (can set up to 10s - higher cost)
- About 15 health checkers will check the endpoint health
- One request every 2 seconds on average
- Can have HTTP, TCP and HTTPS health checks (no SSL verification)
- Possibility of integrating the health check with CloudWatch

- Health checks can be linked to Route53 DNS queries.

![](2019-12-30-10-28-13.png)

![](2019-12-30-10-29-14.png)
