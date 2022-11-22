---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/redshift, database, data-warehouse, review]
sr-due: 2022-12-18
sr-interval: 26
sr-ease: 250
---

# Redshift

- Redshift is based on [[PostgreSQL]], but it's not used for [[OLTP]]
- It's [[OLAP]] - online analytical processing (analytics and data warehousing)
- 10x better performance than other data warehouses, scale to PBs of data
- [[Massively Parrallel Query Execution (MPP)]], [[highly available]]
- Pay as you go based on the instances provisioned
- Has a [[SQL]] interface for performing the queries
- BI tools such as [[AWS Quicksight]] or [[Tableau]] integrate with it

- Data is loaded from [[AWS S3]], [[Programming/AWS/DynamoDB/DynamoDB]], [[Amazon DMS]], other DBs
- From 1 node to 128 nodes, up to 160GB of space for node
- Leader node: for [[query planning]], [[results aggregation]]
- Compute node: for performing the queries, send results to leader
- [[Redshift Spectrum]]: perform queries directly against [[AWS S3]] (no need to load)
- Backup & Restore, Security [[VPC]] / [[IAM]] / [[AWS KMS (Key Management Service)]], [[Monitoring]]
- [[Redshift Enhanced VPC Routing]]: COPY / UNLOAD goes through [[VPC]]

![[Redshift for Solutions Architect]]
