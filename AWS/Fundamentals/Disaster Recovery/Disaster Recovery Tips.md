---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/fundamentals/disaster-recovery, review]
sr-due: 2022-11-24
sr-interval: 1
sr-ease: 210
---

## Disaster Recovery Tips

- [[Backup]]
    - [[EBS Snapshot]]s, [[RDS Backups]] / Snapshots etc
    - Regular pushes to [[AWS S3]] / [[S3 Standard-Infrequent Access (IA) Tier]] / [[S3 Glacier]], [[S3 Lifecycle rules]], [[S3 Cross region replication]]
    - From on-premise: [[AWS Snowball]] or [[AWS Storage Gateway]]
- [[High Availability]]
    - Use [[AWS Route 53]] to migrate [[DNS]] over from Region to Region
    - [[RDS Multi AZ (Disaster Recovery)]], [[ElastiCache Multi-AZ]], [[EFS - Elastic File System]], [[AWS S3]]
    - [[Site to Site VPN]] as a recovery from [[Direct Connect]]
- Replication
    - [[RDS Replication]] (Cross Region), [[AWS Aurora]] + [[Global Databases]]
    - Database replication from on-premise to [[AWS RDS]]
    - [[AWS Storage Gateway]]
- Automation
    - [[CloudFormation]] / [[Elastic Beanstalk]] to re-create a whole new environment
    - Recover / Reboot [[AWS EC2]] isntances with [[CloudWatch]] if [[CloudWatch Alarm]]s fail
    - [[AWS Lambda]] functions for customised automations
- Chaos
    - Netflix has a "[[simian-army]]" randomly terminating [[AWS EC2]]