# EFS Overview (Elastic File System)

- Managed NFS (network file system) that can be mounted on many EC2 instances
- EFS works with EC2 instances in multi-AZ
- Highly available, scalable, expensive (3xgp2), pay per use

---

Use cases: content management, web serving, data sharing, Wordpress
- Uses NFSv4.1 protocol
- Uses security group to controll access to EFS
- Compatible with Linux based AMI (not windows)
- Encryption at rest using KMS
- POSIX file system (~Linux) that has a standard file API
- File system scales automatically, pay-peruse, no capacity planning.

---

- EFS Scale
    - 1000s of concurrent NFS clients, 10GB+/s throughput
    - Grow to petabyte-scale network file system, automatically
- Performance mode (set at EFS creation time)
    - General purpose (defaullt): latency-sensitive use cases (web server, CMS, etc...)
    - Max I/O - higher latency, throughput, highly parralel (big data, media processing)
- Throughput mode
    - Bursting (1TB = 50MiB/s + burst of up to 100MiB/s)
    - Provisioned: set your throughput regardless of storage size, ex: 1Gib/s for 1TB storage
- Storage Tiers (lifecycle management feature - move file after N days)
    - Standard: for frequently accessed files
    - Infrequent acces (EFS-IA): cost to retrieve files, lower price to store