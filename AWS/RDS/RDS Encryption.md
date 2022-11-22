---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/rds, review]
sr-due: 2022-12-12
sr-interval: 20
sr-ease: 250
---

## RDS Encryption

- [[Encryption at rest]] capability with [[AWS KMS (Key Management Service)]] - [[AES-256]] encryption
- [[SSL certificates]] to encrypt data to [[AWS RDS]] in flight
- To enforce SSL
    - [[PostgreSQL]]: `rds.force_ssl1` in the [[AWS RDS]] console ([[Parameter Groups]])
    - [[MySQL]]: `GRANT USAGE ON *.* TO 'mysqluser'@'%' REQUIRE SSL;`
- To connect using SSL:
    - Provide the [[SSL Trust certificate]] (can be downloaded from AWS)
    - Provide [[SSL options]] when connecting to database