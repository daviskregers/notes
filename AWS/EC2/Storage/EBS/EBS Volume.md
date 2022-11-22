---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/storage/ebs, review]
sr-due: 2022-12-16
sr-interval: 24
sr-ease: 250
---

# What's an EBS volume?

- An EC2 machine loses it's root volume (main drive) when it's manually terminated.
- Unexpected terminations might happen from time to time (aws would email you)
- Sometimes, you need a way to store your instance data somewhere
- An EBS (Elastic Block Store) volume is a network drive you can attach to your instances while they run
- It allows your instances to persist data

## EBS Volume

- It's a network drive (i.e. not a physical drive)
    - It uses the network to communicate the instance, which means there might be a bit of latency
    - It can be detached from an [[AWS EC2]] instance and attached to another one quickly as long as their in the same AZ
- It's locked to an [[Availability Zone]]
    - An EBS Volume in us-east-1a cannot be attached to us-east-1b
    - To move a volume across, you first need to snapshot it
- Have a provisioned capacity (size in GBs and IOPS)
    - You get billed for all the provisioned capacity
    - You can increase the capacity of the drive over time

![[EBS Volume Types]]

![[EBS vs Instance Store]]
![[EBS RAID Options]]

