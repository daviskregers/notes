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
- Postgres and MySQL are both supported as Aurora DB (that means your drivers will work as if Aurora was a Postgres or MySQL database)
- Aurora is "AWS cloud optimized" and claims 5x performance improvement over MySQL on RDS, over 3x the performance of Postgres on RDS.
- Aurora storage automatically grows in increments of 10GB, up to 64TB.
- Aurora can have 15 replicas while MySQL has 5, and the replication process is faster (sub 10 ms replica lag)
- Failover in Aurora is instantaneous. It's High Availability native.
- Aurora costs more than RDS (20% more) - but is more efficient.

## Aurora High Availibility and Read Scaling

- 6 copies of your data accross 3 AZ
    - 4 copies out of 6 needed for writes
    - 3 copies out of 6 needed for reads
    - Self healing with peer-to-peer replication
    - Storage is striped accross 100s of volumes
- One aurora instance takes writes (master)
- Automated failover for master in less than 30 seconds
- Master + up to 15 aurora read replica serve reads
- Support for Cross Region Replication

![](2019-12-30-09-16-14.png)

## Aurora DB Cluster

![](2019-12-30-09-17-11.png)

## Features of Aurora

- Automatic fail-over
- Backup and recovery
- Isolation and security
- Industry compliance
- Push-button scaling
- Automated Patching with Zero Downtime
- Advanced Monitoring
- Routine Maintenance
- Backtrack: restore data at any point of time without using backups.

## Aurora Security

- Encryption at rest using KMS
- Automated backups, snapshots and replicas are also encrypted
- Encryption in flight using SSL (same process as MySQL or Postgres)
- Authentication using IAM
- You are responsible for protecting the instance with security groups
- You can't SSH

## Aurora Serverless

- No need to choose an isntance size
- Only supports MySQL 5.6 (as of Jan 2019) & Postgres (beta)
- Helpful when you can't predict workload
- DB cluster starts, shutdown and scales automatically based on CPU / connections
- Can migrate from Aurora Cluster to Aurora serverless and vice versa
- Aurora serverless usage is measured in ACU (Aurora Capacity Units)
- Billed in 5 minutes increment of ACU
- Note: Some features of aurora aren't supported in serverless mode, be sure to check the documentation if you plan on using it.

## Aurora for Solutions Architects

- Can use IAM authentication for Aurora MySQL and Postgres
- Aurora Global databases span multiple regions and enable Disaster Recovery
    - One primary region
    - One DR region
    - The DR region can be used for lower latency reads
    - < 1 second replica lag on average
- If not using Global Databases, you can create cross-region read replicas
    - But the FAQ recommends you using Global Databases instead