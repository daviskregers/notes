---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/s3/storage-gateway, review]
sr-due: 2022-12-12
sr-interval: 20
sr-ease: 250
---

## Volume Gateway

- Block storage using [[iSCSI]] protocol backed by [[AWS S3]]
- Backed by [[EBS Snapshot]]s which can help restore [[on-premise volume]]s
- [[Cached volume]]s: low latency access to most recent data
- [[Stored volume]]s: entire dataset is on premise, scheduled backups to [[AWS S3]]