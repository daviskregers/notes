# EBS Overview

## What's an EBS Volume?

- An EBS (Elastic Block Storage) Volume is a network drive you can attach to your instances while they run
- It allows your instances to persist data, event after their termination
- They can only be mounted to one instance at a time (at the Certified Cloud Practicioner level, for Solutions Architect, Developer, SysOpes - there is multi-attach feature for some EBS).
- They are bound to a specific availability zone

Free tier: 30 GB of free EBS storage of type General Purpose (SSD) or Magnetic per month.

## EBS Volume

- It's a network drive (i.e. not a physical drive)
    - It uses the network to communicate to the instance, which means there might be a bit of latency
    - It can be detached from an EC2 instance and attached to another one quickly
- It's locked to an Availability Zone (AZ)
    - An EBS Volume in us-east-1a cannot be attached to us-east-1b
    - To move a volume across, you first need to snapshot it
- Have a provisioned capacity (size in GBs, and IOPS)
    - You get billed for all the provisioned capacity
    - You can increase the capacity of the drive over time

## EBS - Delete on Termination attribute

When creating EC2 instances, there is an option to choose `Delete on Termination` option, which will delete the EBS volume once the instance is terminated.

By default it is enabled for the root volume, but isn't for any custom added volume.