---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/rds/aurora, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

## Aurora Serverless

- No need to choose an instance size
- Only supports MySQL 5.6 (as of Jan 2019) & PostgreSQL (beta)
- Helpful when you can't predict workload
- DB cluster starts, shutdown and scales automatically based on CPU / connections
- Can migrate from [[Aurora DB Cluster]] to [[AWS Aurora]] serverless and vice versa
- Aurora serverless usage is measured in ACU (Aurora Capacity Units)
- Billed in 5 minutes increment of ACU
- Note: Some features of aurora aren't supported in [[serverless]] mode, be sure to check the documentation if you plan on using it.

NOTE: aurora serverless v2 supports MySQL 8 now