# AWS Shared Responsibility Model

- AWS responsibility - Security of the Cloud
    - Protecting infrastructure (hardware, software, facilities, and networking) that runs all of the AWS services
    - Managed services like S3, DynamoDB, RDS etc
- Customer responsibility - Security in the Cloud
    - For EC2 instance, customer is responsible for management of the guest OS (including security patches and updates), firewall & network configuration, IAM etc

## Example for RDS

- AWS responsibility
    - Manage the underlying EC2 instance, disable SSH access
    - Automated DB patching
    - Automated OS patching
    - Audit the underlying instance and disks & guarantee it functions
- Your responsibility
    - Check the ports / IP / security group inbound rules in DB's SG
    - In-database user creation and permissions
    - Creating a database with or without public access
    - Ensure parameter groups or DB is configured to only allow SSL connections
    - Database encryption testing

## Example for S3

- AWS responsibility
    - Guarantee you get unlimited storage
    - Guarantee you get encryption
    - Ensure separation of the data between different customers
    - Ensure AWS employees can't access your data
- Your responsibility
    - Bucket configuration
    - Bucket policy / public settings
    - IAM user and roles
    - Enabling encryption

![](2020-01-01-15-25-57.png)