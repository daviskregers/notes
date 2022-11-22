---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/rds, database, review]
sr-due: 2023-01-08
sr-interval: 48
sr-ease: 270
---



# AWS RDS Overview

- RDS stands for [[Relational Database]] Service
- It's a manager DB service for DB use SQL as as a query language
- It allows you to create databases in the cloud that are managed by AWS
    - [[PostgreSQL]]
    - [[Oracle]]
    - [[MySQL]]
    - [[MariaDB]]
    - [[Microsoft SQL Server]]
    - [[AWS Aurora]] (AWS Proprietary database)

- Must provision an [[AWS EC2]] instance & [[EBS Volume]] type and size
- Support for [[Read Replica]]s and [[Multi AZ]]
- Security through [[IAM]], [[Security Group]]s, [[AWS KMS (Key Management Service)]], [[SSL]] in transit
- [[Backup]] / [[Snapshot]] / [[Point in time restore]] feature
- Managed and Scheduled maintenance
- Monitoring though [[CloudWatch]]

---

- Use case: store relational datasets ([[RDBMS]]/[[OLTP]]), perform queries, transactional inserts / update / delete is available.


![[ RDS vs DB on EC2 ]]

![[RDS Read replicas for read scalability]]

![[RDS Multi AZ (Disaster Recovery)]]


![[RDS Backups]]

![[RDS Encryption]]

![[RDS Security]]

![[RDS vs Aurora]]

![[RDS for Solutions Architect]]
