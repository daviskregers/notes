# EBS Multi-Attach - io1/io2 family

- Attach the same EBS volume to multiple EC2 instances in the same AZ
- Each instance has full read&write permissions to the volume
- Use case
    - Achieve higher application availability in clustered Linux applications (ex: Teradata)
    - Applications must manage concurrent write opperations
- Must use a file system that's cluster aware:
    - Not XFS, EX4 etc