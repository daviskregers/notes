---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/elastic-loadbalancer, development/aws/solutions-architect, review]
sr-due: 2022-12-05
sr-interval: 18
sr-ease: 250
---

## Auto Scaling Groups For Solutions Architects

- [[ASG Default Termination Policy]] (simplified version)
    - Find the AZ which has the most number of instances
    - If there are multiple instances in the [[Availability Zone]]s to choose from, delete the one with the oldest configuration
- ASG tries the balance the number of instances across [[Availability Zone]]s by default

- The [[cool-down period]] helps to ensure that your Auto Scaling group doesn't launch or terminate additional instances before the previous scaling activity takes effect.
- In addition to default cool-down for [[Auto Scaling Group (ASG)]], we can create cool-downs that apply to a specific [[simple scaling policy]]
- A scaling-specific cool-down period overrides the [[default cool-down period]]
- One common use for scaling-specific cool-downs is with a [[scale-in policy]] - a policy that terminates instances based on a specific criteria or metric. Because this policy terminates instances, [[Amazon EC2 Auto Scaling]] needs less time to determine whether to terminate additional instances.
- If the default cool-down period of 300 seconds is too long - you can reduce costs by applying a scaling-specific cool-down period of 180 seconds to the [[scale-in policy]].
- If your application is scaling up and down multiple times each hour, modify the auto scaling groups cool-down timers and the cloud watch alarm period that triggers the [[Scale in]]