---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/cloudwatch, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# CloudWatch Alarms

- Alarms are used to trigger notifications for any [[metric]]
- Alarms can go to [[Auto Scaling Group (ASG)]], [[EC2 actions]], [[SNS notifications]]
- Various options (sampling, %, max, min, etc)
- Alarm States:
    - OK
    - INSUFFICIENT_DATA
    - ALARM
- Period:
    - Length of time in seconds to evaluate the metric
    - High resolution custom metrics: can only choose 10 sec or 30 sec

![](2020-01-01-13-55-37.png)