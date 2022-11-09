---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/rds, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

## RDS Security

- RDS databases are usually deployed within a [[private subnet]], not a [[public subnet]]
- RDS security works by leveraging [[Security Group]]s (the same concept as for [[AWS EC2]] instances) - it controls who can communicate with [[AWS RDS]].
- [[IAM Policy]] help control who can manage [[AWS RDS]]
- Traditional Username and Password can be used to login to the database
- [[IAM user]]s can now be used too (for [[MySQL]] / [[AWS Aurora]])