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

## AWS CloudWatch Custom metrics

- Possibility to define and send your own custom metrics to [[CloudWatch]]
- Ability to use dimensions (attributes) to segment metrics
    - Instance.id
    - Environment.name
- Metric resolution
    - Stanard: 1 minute
    - High Resolution: up to 1 second (storageResolution API parameter) - higher cost
- Use API call PutMetricData
- Use exponential back off in case of throttle errors

![](2020-01-01-13-58-34.png)