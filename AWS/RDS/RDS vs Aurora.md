---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/rds, database, review]
sr-due: 2022-12-13
sr-interval: 21
sr-ease: 250
---

## RDS vs Aurora

- [[AWS Aurora]] is a [[proprietary technology]] from AWS (not open sourced)
- [[PostgreSQL]] and [[MySQL]] are both supported as [[AWS Aurora]] DB (that means your drivers will work as if Aurora was a Postgres or MySQL database)
- [[AWS Aurora]] is `AWS cloud optimized` and claims 5x performance improvement over [[MySQL]] on [[AWS RDS]], over 3x the performance of Postgres on RDS.
- Aurora storage automatically grows in increments of 10GB up to 64TB.
- Aurora can have 15 [[Read Replica]]s while [[MySQL]] has 5, and the replication process is faster (sub 10 ms replica lag).
- [[Failover]] in Aurora is instantaneous. It's High Availability native.
- Aurora costs more than RDS (20% more) - but it's more efficient.