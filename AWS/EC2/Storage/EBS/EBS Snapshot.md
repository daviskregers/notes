---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/storage/ebs, review]
sr-due: 2022-12-17
sr-interval: 25
sr-ease: 250
---

## EBS Snapshots

- Incremental - only backups changed blocks
- EBS Backups use [[IO]] and you shouldn't run them while your application is handling a lot of traffic
- [[Snapshots]] will be stored in [[AWS S3]] (but you won't directly see them)
- Not necessary to detach volume to do snapshot, but recommended
- Max 100,000 snapshots
- Can copy snapshots across [[Availability Zone]] or [[AWS Region]]
- Can make Image ([[EC2 AMIs]]) from snapshot
- **[[EBS Volume]] restored by snapshots need to be pre-warmed (using [[fio]] or [[dd]] command to read the entire volume)**
- **Snapshots can be automated using [[Amazon Data Lifecycle Manager]]**

The snapshots can be created by right-clicking on the volume.

![](2019-12-30-07-15-22.png)

![](2019-12-30-07-16-44.png)

![](2019-12-30-07-17-09.png)

When the snapshot is created we can do several operations with it:
- Create a new volume from the snapshot
- Create Image ([[EC2 AMIs]]) from the snapshot

![](2019-12-30-07-18-12.png)

We can also go to the `Lifecycle Manger` section and add a new snapshot policy, like we are going to make snapshots for all the volumes that have a tag `EBS Demo` every 12 hours and keep the last 7 copies.

![](2019-12-30-07-21-32.png)

