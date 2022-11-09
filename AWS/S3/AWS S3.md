---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/s3, database, serverless, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# Amazon S3

- Amazon S3 is one of the main building blocks of AWS
- It's advertised as "infinitely scaling" storage
- It's widely popular

- Many websites use AWS S3 as a backbone
- Many AWS services uses AWS S3 as an integration as well


- S3 is a key/value store for objects
- Great for big objects, not so great for small objects
- [[Serverless]], scales infinitely, max object size is 5TB
- [[Eventual consistency]] for overwrites and deletes
- Tiers: [[S3 Standard Tier (General Purpose)]], [[S3 Standard-Infrequent Access (IA) Tier]], [[S3 One Zone-Infrequent Access (IA) Tier]], [[S3 Glacier]] for backups
- Security: [[IAM]], [[bucket policy]], [[ACL]]
- Encryption: [[SSE-S3]], [[SSE-KMS]], [[SSE-C]], [[S3 Client Side Encryption]], [[SSL in transit]]

Use case: static files, key value store for big files, website hosting.

![[S3 For Solutions Architect]]
