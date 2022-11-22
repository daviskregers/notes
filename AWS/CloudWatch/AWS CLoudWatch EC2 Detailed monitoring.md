---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/cloudwatch, review]
sr-due: 2022-12-16
sr-interval: 24
sr-ease: 250
---

## AWS CloudWatch EC2 Detailed monitoring

- [[AWS EC2]] instance metrics have metrics "every 5 minutes"
- With detailed monitoring (for a cost), you get data "every 1 minute"
- Use detailed monitoring if you want to more prompt scale your [[Auto Scaling Group (ASG)]]
- The AWS Free Tier allows us to have 10 detailed monitoring metrics

- Note: [[AWS EC2]] Memory usage is by default not pushed (must be pushed from inside the instance as a custom metric)