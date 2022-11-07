# What's an EBS volume?

- An EC2 machine loses it's root volume (main drive) when it's manually terminated.
- Unexpected terminations might happen from time to time (aws would email you)
- Sometimes, you need a way to store your instance data somewhere
- An EBS (Elastic Block Store) volume is a network drive you can attach to your instances while they run
- It allows your instances to persist data

## EBS Volume

- It's a network drive (i.e. not a physical drive)
    - It uses the network to communicate the instance, which means there might be a bit of latency
    - It can be detached from an ec2 instance and attached to another one quickly as long as their in the same AZ
- It's locked to an AZ (Availability Zone)
    - An EBS Volume in us-east-1a cannot be attached to us-east-1b
    - To move a volume accross, you first need to snapshot it
- Have a provisioned capacity (size in GBs and IOPS)
    - You get billed for all the provisioned capacity
    - You can increase the capacity of the drive over time

## EBS Volume Types

- EBS Volumes come in 4 Types:
    - GP2 (SSD): General purpose SSD volume that balances price and performance for a wide variety of workloads
        - Reccomended for most workloads
            - System boot volumes
            - Virtual desktops
            - Low latency interactive apps
            - Development and test environments
        - 1 GiB - 16 TiB capacity
        - Small gp2 volumes can burst IOPS to 3000
        - Max IOPS is 16000
        - 3 IOPS per GB, means at 5334GB we are at the max IOPS
    - IOI (SSD): Highest performance SSD volume for mission-critical low-latency or high throughput workloads
        - Critical business applications that require sustained IOPS performance, or more than 16000 IOPS per volume (gp2 limit)
        - Large database workloads such as
            - MongoDB, Cassandra, Microsoft SQL Server, MySQL, PostgreSQL, Oracle
        - 4 GiB - 16TiB
        - IOPS is provisioned (PIOPS) - Min 100 - Max 64'000 (Nitro instances) else MAX 32'000 (other instances)
        - The maximum ratio of provisioned IOPS to requested volume size (in GiB) is 50:1. (For each GiB we can request 50 IOPS).
    - STI (HDD): Low cost HDD volume designed for frequently accessed, throughput intensive workloads
        - Streaming workloads requiring consistent, fast throughput at low price.
        - Big data, Data warehouses, Log processing
        - Apache Kafka
        - Cannot be a boot volume
        - 500GiB - 16TiB
        - Max IOPS is 500
        - Max Throughput of 500MiB/s - can burst
    - SCI (HDD): Lowest cost HDD volume designed for less frequently accessed workloads
        - Throughput-oriented storage for large volumes of data that is infrequently accessed
        - Scenarios where the lowest storage cost is important
        - Cannot be a boot volume
        - 500 GiB - 16 TiB
        - Max IOPS is 250
        - Max throughput of 250 MiB/s - can burst
- EBS Volumes are characterized in Size | Throughput | IOPS (I/O Ops per sec)
- When in doubt always consult with the AWS documentations.
- Only GP2 and IOI can be used as boot volumes.

## EBS vs Instance Store

- Some instances do not come with Root EBS volumes
- Instead, they come with "Instance Store" (= ephemeral storage)
- Instance store is physically attached to the machine (EBS is a network drive)
- Pros:
    - Better I/O performance
    - Good for buffer / cache / scratch data / temporary content
    - Data survives reboots
- Cons:
    - On stop or termination, the instance store is lost
    - You can't resize the instance store
    - Backups must be operated by the user

We can see this if we were to launch an instance like `m5ad.2xlarge` that has a 300 GB SSD.

![](2019-12-30-07-36-16.png)

## EBS RAID Options

- EBS is already redundant storage (replicated within AZ)
- But what if you want to increase IOPS to say 100 000 IOPS?
- Whay if you want to mirror your EBS volumes?
- You would mount volumes in parralel in RAID settings.
- RAID is possible as long as your OS supports it
- Some RAID options are:
    - RAID 0
    - RAID 1
    - RAID 5 (not recommended for EBS - see documentation)
    - RAID 6 (not recommended for EBS - see documentation)

### RAID 0 (increase performance)

- Combining 2 or more volumes and getting the total disk space and I/O
- But one disk fails, all the data fails
- Use cases would be:
    - An application that needs a lot of IOPS and doesn't need fault-tolerance
    - A database that has replication already built-in
- Using this, we can have a very big disk wih a lot of IOPS
- For example:
    - two 500 GiB Amazon EBS IO volumes with 4,000 priovisioned IOPS each will create a 1000 GiB RAID 0 array with an available bandwith of 8,000 IOPS and 1,000 MB/s of throughput

### RAID 1 (increase fault tolerance)

- RAID 1 = Mirroring a volume to another
- If one disk fails, our logical volume is still working
- We have to send the data to two EBS volumes at the same time (2x network)
- Use case:
    - Application that needs increased fault tolerance
    - Application where you need to service disks
- For example:
    - Two 500 GiB Amazon EBS IOI volumes with 4,000 provisioned IOPS each will create a 500 GiB RAID 1 array with an available bandwith of 4,000 IOPS and 500 MB/s of throughput.