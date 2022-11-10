---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/rds, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

## Advantage over using RDS vs DB on EC2

- Managed service
    - OS patching level
    - Continuous backups and restore to specific timestamp ([[Point in Time Restore]])
    - Monitoring dashboards
    - Read replicas for improved read performance
    - Multi AZ setup for DR ([[Disaster Recovery]])
    - Maintenance windows for for upgrades
    - Scaling capability ([[Vertical scalability]] and [[Horizontal scalability]])
    - But you can't [[EC2 SSH]] into your instances