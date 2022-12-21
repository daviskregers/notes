---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/rds/aurora, development/aws/solutions-architect, development/database, development/aws/solutions-architect, review]
sr-due: 2022-12-18
sr-interval: 26
sr-ease: 250
---

## Aurora for Solutions Architects

- Can use [[IAM authentication]] for [[AWS Aurora]] [[MySQL]] and [[PostgreSQL]]
- [[Aurora Global]] databases span multiple regions and enable [[Disaster Recovery]]
    - One primary region
    - One DR region
    - The DR region can be used for lower latency reads
    - < 1 second replica lag on average
- If not using Global Databases, you can create cross-region read replicas
    - But the FAQ recommends you using [[Global Databases]] instead

- **Operations**: less operations, [[auto scaling storage]]
- **Security**: AWS responsible for [[OS security]], we are responsible for setting up [[AWS KMS (Key Management Service)]], [[Security Group]]s, [[IAM Policy]], authorising users in DB, using [[SSL]]
- **Reliability**: [[Multi AZ]], [[Programming/AWS/Fundamentals/High Availability]], possibly more than [[AWS RDS]], [[Aurora Serverless]] option.
- **Performance**: 5x performance (according to AWS) due to architectural optimisations. Up to 15 [[Read Replica]]s (only 5 for [[AWS RDS]])

- **Cost**: Pay per hour based on [[AWS EC2]] and storage usage. Possibly lower costs compared to Enterprise grade databases such as [[Oracle]].