# AWS RDS Overview

- RDS Stands for Relatational Database Service
- It's a managed DB service
- It allows you to create databases in the cloud that are managed by AWS
    - Postgresql
    - MySQL
    - MariaDB
    - Oracle
    - Microsoft SQL Server
    - Aurora (AWS PRoprietary Database)

## Advantage over using RDS versus deploying DB on EC2

- RDS is a managed service:
    - Automated provisioning, OS pathching
    - Continous backups and restore to specific timestamp (Point in Time Restore)
    - Monitoring dashboards
    - Read replicas for improved read performance
    - Multi AZ setup for DR (Disaster Recovery)
    - Maintenance windows for upgrades
    - Scaling capability (vertical and horizontal)
    - Storage backed by EBS (gp2 or io1)
- But you cannot SSH into your instances

## RDS Backups

- Backups are automatically enabled in RDS
- Automated backups:
    - Daily full backup of the database (during the maintenance window)
    - Transaction logs are backed-up by RDS every 5 minutes
    - Ability to restore to any point in time (from oldest backup to 5 minutes ago)
    - 7 day retention (can be increased to 35 days)
- DB Snapshots
    - Manually triggered by the user
    - Retention of backup for as long as you want

## RDS - Storage Auto Scaling

- Helps you increase storage on your RDS DB instance dynamically
- When RDS detects you are running out of free database storage, it scales automatically
- Avoid manually scaling your database storage
- You have to set `Maximum Storage Threshold` (maximum limit for DB Storage)
- Automatically modify storage if:
    - Free storage less than 10% of allocated storage
    - Low-storage lasts at least 5 minutes
    - 6 hours have passed since last modification
- Useful for applications with unpredicatable loads
- Supports all RDS database engines (MariaDB, MySQL, PostgreSQL, SQL Server, Oracle).