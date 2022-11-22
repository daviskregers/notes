---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/storage/ebs, review]
sr-due: 2022-12-14
sr-interval: 22
sr-ease: 250
---

## EBS RAID Options

- EBS is already [[redundant storage]] (replicated within AZ)
- But what if you want to increase [[IOPS]] to say 100 000 [[IOPS]]?
- What if you want to mirror your [[EBS volume]]s?
- You would mount volumes in parallel in [[RAID settings]].
- RAID is possible as long as your OS supports it
- Some RAID options are:
    - [[RAID 0]]
    - [[RAID 1]]
    - [[RAID 5]] (not recommended for EBS - see documentation)
    - [[RAID 6]] (not recommended for EBS - see documentation)

### [[RAID 0]] (increase performance)

- Combining 2 or more volumes and getting the total disk space and I/O
- But one disk fails, all the data fails
- Use cases would be:
    - An application that needs a lot of IOPS and doesn't need fault-tolerance
    - A database that has replication already built-in
- Using this, we can have a very big disk wih a lot of [[IOPS]]
- For example:
    - two 500 GiB Amazon EBS IO volumes with 4,000 priovisioned IOPS each will create a 1000 GiB RAID 0 array with an available bandwith of 8,000 IOPS and 1,000 MB/s of throughput

### [[RAID 1]] (increase fault tolerance)

- RAID 1 = Mirroring a volume to another
- If one disk fails, our logical volume is still working
- We have to send the data to two EBS volumes at the same time (2x network)
- Use case:
    - Application that needs increased fault tolerance
    - Application where you need to service disks
- For example:
    - Two 500 GiB Amazon EBS IOI volumes with 4,000 provisioned IOPS each will create a 500 GiB RAID 1 array with an available bandwidth of 4,000 IOPS and 500 MB/s of throughput.