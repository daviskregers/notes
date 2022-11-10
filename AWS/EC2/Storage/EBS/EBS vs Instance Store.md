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

## EBS vs [[EC2 Instance Store]]

- Some instances do not come with Root EBS volumes
- Instead, they come with "[[EC2 Instance Store]]" (= ephemeral storage)
- Instance store is physically attached to the machine (EBS is a network drive)
- Pros:
    - Better [[I/O performance]]
    - Good for [[buffer]] / [[cache]] / [[scratch data]] / [[temporary content]]
    - Data survives reboots
- Cons:
    - On stop or termination, the [[EC2 Instance Store]] is lost
    - You can't resize the instance store
    - Backups must be operated by the user

We can see this if we were to launch an instance like `m5ad.2xlarge` that has a 300 GB SSD.

![](2019-12-30-07-36-16.png)
