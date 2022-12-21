---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/rds/aurora, development/database, development/aws/solutions-architect, review]
sr-due: 2023-01-15
sr-interval: 54
sr-ease: 270
---

# Aurora overview

- Aurora is a proprietary technology from AWS (not open sourced)
- [[PostgreSQL]] and [[MySQL]] are both supported as Aurora DB (that means your drivers will work as if Aurora was a PostgreSQL or MySQL database)
- Aurora is "AWS cloud optimized" and claims 5x performance improvement over MySQL on RDS, over 3x the performance of PostgreSQL on RDS.
- Aurora storage automatically grows in increments of 10GB, up to 64TB.
- Aurora can have 15 replicas while MySQL has 5, and the replication process is faster (sub 10 ms replica lag)
- Failover in Aurora is instantaneous. It's [[Programming/AWS/Fundamentals/High Availability]] native.
- Aurora costs more than RDS (20% more) - but is more efficient.

- Auto healing capability
-[[ Multi AZ]], Auto Scaling [[Read Replica]]s
- [[Read Replica]]s can be Global
- Aurora database can be Global for [[Disaster Recovery]] or [[latency]] purposes
- Auto scaling of storage from 10GB to 64 TB
- Define [[AWS EC2]] instance type for aurora instances
- Same security / monitoring / maintenance features as [[RDS Security]]
- [[Aurora Serverless]] option

---

Use case: same as [[AWS RDS]], but with less maintenance / more flexibility / more performance

![[Aurora For Solutions Architects]]

![[ Aurora DB Cluster]]

![[Aurora Security]]

![[ Aurora Serverless]]

![[ Aurora For Solutions Architects ]]


![[Aurora High Availability and Read Scaling]]