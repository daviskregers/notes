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

# Aurora overview

- Aurora is a proprietary technology from AWS (not open sourced)
- [[PostgreSQL]] and [[MySQL]] are both supported as Aurora DB (that means your drivers will work as if Aurora was a PostgreSQL or MySQL database)
- Aurora is "AWS cloud optimized" and claims 5x performance improvement over MySQL on RDS, over 3x the performance of PostgreSQL on RDS.
- Aurora storage automatically grows in increments of 10GB, up to 64TB.
- Aurora can have 15 replicas while MySQL has 5, and the replication process is faster (sub 10 ms replica lag)
- Failover in Aurora is instantaneous. It's [[High Availability]] native.
- Aurora costs more than RDS (20% more) - but is more efficient.

## Aurora [[High Availibility]] and [[Read Scaling]]

- 6 copies of your data across 3 [[Availability Zone]]
    - 4 copies out of 6 needed for writes
    - 3 copies out of 6 needed for reads
    - Self healing with peer-to-peer replication
    - Storage is striped across 100s of volumes
- One aurora instance takes writes (master)
- Automated failover for master in less than 30 seconds
- Master + up to 15 aurora read replica serve reads
- Support for [[Cross Region Replication]]

![](2019-12-30-09-16-14.png)

![[ Aurora DB Cluster]]

![[ Aurora Features ]]

![[Aurora Security]]

![[ Aurora Serverless]]

![[ Aurora For Solutions Architects ]]