---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ecs, review]
sr-due: 2022-12-06
sr-interval: 9
sr-ease: 150
---

- [[ECS Config file]] is at `/etc/ecs/ecs.config`

```conf
ECS_CLUSTER=MyCluster # Assign EC2 instance to an ECS cluster
ECS_ENGINE_AUTH_DATA={...} # to pull images from private registries
ECS_AVAILABLE_LOGGING_DRIVERS=[...] # CloudWatch container logging
ECS_ENABLE_TASK_IAM_ROLE=true # Enable IAM roles for ECS tasks
```