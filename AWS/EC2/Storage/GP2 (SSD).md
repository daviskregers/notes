---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/storage/ebs, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

GP2 (SSD): General purpose SSD volume that balances price and performance for a wide variety of workloads

- Recommended for most workloads
	- System boot volumes
	- Virtual desktops
	- Low latency interactive apps
	- Development and test environments
- 1 GiB - 16 TiB capacity
- Small gp2 volumes can burst IOPS to 3000
- Max IOPS is 16000
- 3 IOPS per GB, means at 5334GB we are at the max IOPS