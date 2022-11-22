---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/s3/storage-gateway, review]
sr-due: 2022-12-15
sr-interval: 23
sr-ease: 250
---

![[ Hybrid Cloud Storage ]]


## AWS Storage Gateway

- Bridge between on-premise data and cloud data in [[AWS S3]]
- Use cases: [[disaster recovery]], backup & restore, [[Tiered storage]]
- 3 types of Storage Gateway

![[File Gateway]]

![[Volume Gateway]]

![[Tape Gateway]]


- File access / [[NFS]] => [[File Gateway]] (backed by [[AWS S3]])
- Volumes / [[Block Storage]] / [[iSCSI]] => [[Volume gateway]] (backed by [[AWS S3]] with [[EBS Snapshot]]s)
- [[VTL Tape]] solution / Backup with [[iSCSI]] => [[Tape Gateway]] (backed by [[AWS S3]] and [[S3 Glacier]])