---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/rds/aurora, development/aws/solutions-architect, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

## Aurora [[High Availability]] and [[Read Scaling]]

- 6 copies of your data across 3 [[Availability Zone]]
    - 4 copies out of 6 needed for writes
    - 3 copies out of 6 needed for reads
    - Self healing with peer-to-peer [[replication]]
    - Storage is [[striped]] across 100s of volumes
- One [[AWS Aurora]] instance takes writes (master)
- Automated [[failover]] for master in less than 30 seconds
- Master + up to 15 aurora read replica serve reads
- Support for [[Cross Region Replication]]

![](2019-12-30-09-16-14.png)