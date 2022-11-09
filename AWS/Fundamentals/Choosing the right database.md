---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/fundamentals]
---

# Choosing the right database

- We have a lot of managed databases on AWS to choose from
- Questions to choose the right [[database]] based on your [[architecture]]
    - [[Read-heavy]], [[write-heavy]], or [[balanced workload]]? [[Throughput]] needs? Will it change, does it need to scale or fluctuate during the day?
    - How much data to store and for how long? Will it grow? Average object size? How are they accessed?
    - [[Data durability]]? [[Source of truth]] for the data?
    - [[Latency]] requirements? [[Concurrent users]]?
    - [[Data model]]? How will you query the data? Joins? Structured? Semi-Structured?
    - [[Strong schema]]? More flexibility? Reporting? Search? [[RBDMS]] / [[NoSQL]]?
    - License costs? Switch to Cloud Native DB such as Aurora?

## Database types

- [[RDBMS]] (= [[SQL]]/[[OLTP]]): [[AWS RDS]], [[AWS Aurora]] - great for joins
- [[NoSQL]] database: [[Programming/AWS/DynamoDB/DynamoDB]] (~[[JSON]]), [[ElastiCache]] (key/value pairs), [[~ Inbox/Neptune]] ([[graphs]]) - no joins, no SQL
- [[Object Store]]: [[AWS S3]] (for big objects) / [[S3 Glacier]] (for backups / archives)
- [[Data Warehouse]] (= [[SQL Analytics]] / [[BI]]): [[~ Inbox/Redshift]] ([[OLAP]]), [[AWS Athena]]
- [[Search]]: [[ElasticSearch]] ([[JSON]]) - [[free text]], [[unstructured searches]]
- [[Graphs]]: [[~ Inbox/Neptune]] - display relationships between data

