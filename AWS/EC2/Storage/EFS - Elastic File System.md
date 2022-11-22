---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/storage/efs, review]
sr-due: 2022-12-13
sr-interval: 21
sr-ease: 250
---

# EFS - Elastic File System

- Managed [[NFS (network file system)]] that can be mounted on many [[AWS EC2]]
- EFS works with EC2 instances in multi-AZ
- Highly available, scalable, expensive (3x[[GP2 (SSD)]]), pay per use
- Use cases:
    - Content management
    - Web serving
    - Data sharing
    - Wordpress
- Uses [[NFSv4.1]] protocol
- Uses [[Security Group]] to control access to EFS
- Compatible with Linux based AMI (not Windows)
- Performance mode:
    - General purpose (default)
    - MAX I/O  - used when thousands of [[AWS EC2]] are using the [[Elastic File System (EFS)]]
- EFS file sync to sync from on-premise file system to EFS
- Backup EFS-to-EFS (incremental - can choose frequency)
- [[Server side encryption at rest]] using [[AWS KMS (Key Management Service)]]

![](2019-12-30-07-45-31.png)