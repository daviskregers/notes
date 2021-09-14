# EBS vs EFS

- EBS volumes
    - can be attached to only one instance at a time
    - are locked at the Availability Zone (AZ) level
    - gp2: IO increases if the disk size increases
    - io1: can increase IO independently
    - To migrate an EBS volume accross AZ
        - take a snapshot
        - Restore the snapshot to another AZ
        - EBS backups use IO and you shouldn't run them while your application is handling a lot of traffic
    - Root EBS volumes of instances get terminated by default if the EC2 instance gets terminated. (you can disable that).

- EFS volumes
    - Mounting 100s of instances accross AZ
    - EFS share website files (wordpress)
    - Only for linux instances (POSIX)
    - EFS has a higher price point than EBS
    - Can leverage EFS-IA for cost savings

Rembmer: EFS vs EBS vs Instance Store