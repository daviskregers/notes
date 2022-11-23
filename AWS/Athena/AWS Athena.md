---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/athena, database, review]
sr-due: 2022-12-17
sr-interval: 25
sr-ease: 250
---

# Athena overview

- [[Serverless]] service to perform analytics directly against [[S3]] files
- Uses [[SQL]] language to query the files
- Has a [[JDBC]] / [[ODBC]] driver
- Charged per query and amount of data scanned
- Supports [[CSV]], [[JSON]], [[ORC]], [[Avro]] and [[Parquet]] (built on [[Presto]])
- Use cases: [[Business intelligence]] / analytics / reporting, analyze & query [[VPC Flow Logs + Athena]], [[ Load Balancer Logs ]], [[CloudTrail]] trails etc

- Fully [[Serverless]] database with [[SQL]] capabilities
- Used to query data in [[AWS S3]]
- Pay per query
- Output results back to [[AWS S3]]
- Secured though [[IAM]]

---

Use case: one time SQL queries, [[Serverless]] queries on [[AWS S3]], [[log analytics]]

![[Athena for Solutions Architect]]
