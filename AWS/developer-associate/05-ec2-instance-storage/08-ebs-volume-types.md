# EBS Volume Types

- EBS Volumes come in 6 types
    - gp2 / gp3 (SSD): General purpose SSD volume that balances price and performance for a wide variety of workloads
    - io1 / io2 (SSD): Highest performance SSD volume for mission-critical low latency or high-throughput workloads
    - st1 (HDD): Low cost HDD volume designed for frequently accessed, throughput-intensive workloads
    - sc1 (HDD): Lowest cost HDD volume designed for less frequently accessed workloads
- EBS Voluimes are characterized in Size | Thoughput | IOPS
- When in doubt always consult the AWS documentation
- Only gp2/gp3 and io1/io2 can be used as boot volumes

## General Purpose SSD

- Cost efective storage, low latency
- System boot volumes, Virtual desktops, Development and test environments
- 1 GiB - 16 TiB
- gp3:
    - Baseline of 3000 IOPS and throughput of 125MiB/s
    - Can increase IOPS up to 16000 and throughput up to 1000MiB/s independently
- gp2:
    - Small gp2 volumes can burst IOPS to 3000
    - Size of the volume and IOPS are linked, max IOPS is 16,000
    - 3 IOPS per GB, means at 5334 GB we are at the max IOPS

## Provisioned IOPS (PIOPS) SSD

- Critical business application with sustained IOPS performance
- Or applications that need more than 16000 IOPS
- Great for database workloads (sensitive to storage performance and consistency)
- io1/io2 (4GiB-16TiB):
    - Max PIOPS: 64000 for Nitro EC2 instances & 32000 for other
    - Can increase PIOPS independently from storage size
    - io2 have more durability and more IOPS per GiB (at the same price as io1)
- io2 Block Express (4 GiB - 64TiB):
    - sub-millisecond latency
    - max PIOPS: 256000 with an IOPS:GiB ratio of 1,000:1
- Support EBS multi-attach

## Hard Disk Drives (HDD)

- Cannot be a boot volume
- 125 MiB to 16 TiB
- Throughput optimized HDD (st1)
    - Big Data, Data Warehouses, Log Processing
    - Max throughput 500MiB/s - max IOPS 500
- Cold HDD (sc1):
    - For data that is infrequently accessed
    - Scenarios where lowest cost is important
    -  Max throughput 250MiB/s - Max IOPS 250