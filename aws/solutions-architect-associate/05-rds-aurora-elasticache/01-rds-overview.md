# AWS RDS Overview

- RDS stands for Relational Database Service
- It's a manager DB service for DB use SQL as as a query language
- It allows you to create databases in the cloud that are managed by AWS
    - Postgres
    - Oracle
    - MySQL
    - MariaDB
    - Oracle
    - Microsoft SQL Server
    - Aurora (AWS Proprietary database)

## Advantage over using RDS vs DB on EC2

- Managed ervice
    - OS patching level
    - Continuous backups and restore to specific timestamp (Point in Time Restore)
    - Monitoring dashboards
    - Read replicas for improved read performance
    - Multi AZ setup for DR (Disaster Recovery)
    - Maintenance windows for for upgrades
    - Scaling capability (vertical and horizontal)
    - But you can't SSH into your instances

## RDS Read replicas for read scalability

- Up to 5 Read replicas
- Within AZ, Cross AZ or Cross Region
- Replication is ASYNC, so reads are eventually consistent.
- Applications must update the connection string to leverage read replicas

![](2019-12-30-08-26-23.png)

## RDS Multi AZ (Disaster Recovery)

- SYNC replication
- One DNS name - automatic app failover to standby
- Increase availability
- Failover in case of loss of AZ, loss of network, instance or storage failure
- No manual intervention in apps
- Not used for scaling

![](2019-12-30-08-27-54.png)

## RDS Backups

Backups are automatically enabled in RDS

- Automated backups:
    - Daily full snapshot of the database
    - Capture transaction logs in real time
    - Ability to restore to any point in time
    - 7 days retention (can be increased to 35 days)

- DB snapshots
    - Manually triggered by the user
    - Retention of backup for as long as you want

## RDS Encryption

- Encryption at rest capability with AWS KMS - AES-256 encryption
- SSL certificates to encrypt data to RDS in flight
- To enforce SSL
    - PostgreSQL: `rds.force_ssl1` in the AWS RDS console (Parameter Groups)
    - MySQL: `GRANT USAGE ON *.* TO 'mysqluser'@'%' REQUIRE SSL;`
- To connect using SSL:
    - Provide the SSL Trust certificate (can be downloaded from AWS)
    - Provide SSL options when connecting to database

## RDS Security

- RDS databases are usually deployed within a private subnet, not a public one
- RDS security works by leveraging security groups (the same concept as for EC2 instances) - it controls who can communicate with RDS.
- IAM policies help control who can manage AWS RDS
- Traditional Username and Password can be used to login to the database
- IAM users can now be used too (for MySQL / Aurora)

## RDS vs Aurora

- Aurora is a proprietary technology from AWS (not open sourced)
- Postgres and MySQL are both supported as Aurora DB (that means your drivers will work as if Aurora was a Postgres or MySQL database)
- Autora is `AWS cloud optimized` and claims 5x performance improvement over MySQL on RDS, over 3x the performance of Postgres on RDS.
- Aurora storage automatically grows in increments of 10GB up to 64TB.
- Autora can have 15 replicas while MySQL has 5, and the replication process is faster (sub 10 ms replica lag).
- Failover in Aurora is instantaneous. It's High Availability native.
- Aurora costs more than RDS (20% more) - but it's more efficient.

