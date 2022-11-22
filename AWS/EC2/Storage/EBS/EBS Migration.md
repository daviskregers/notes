---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/storage/ebs, review]
sr-due: 2023-01-10
sr-interval: 49
sr-ease: 270
---

## EBS Migration

- [[EBS Volume]]s are only locked to a specific [[Availability Zone]]
- To migrate it to a different [[Availability Zone]] (or [[AWS Region]]):
    - Snapshot the volume
    - (optional) Copy the volume to a different region
    - Create a volume from the snapshot in the AZ of your choice

![](2019-12-30-07-24-15.png)
![](2019-12-30-07-24-36.png)
![](2019-12-30-07-25-11.png)

