# AWS EC2 Instance Metadata

- AWS EC2 Instance Metadata is powerful but one of the least known features to developers
- It allows AWS EC2 instances to "learn about themselves" without using an IAM Role for that purpose
- The URL is http://169.254.169.254/latest/meta-data
- You can retrieve the IAM Role name from the metadata, but you cannot retrieve the IAM Policy
- Metadata - info about the EC2 instance
- Userdata - launch script of the EC2

This meta data will only work when running from an EC2 instance, will not work on your local computer.

```
[ec2-user@ip-172-31-44-74 ~]$ curl http://169.254.169.254/latest/meta-data
ami-id
ami-launch-index
ami-manifest-path
block-device-mapping/
events/
hostname
identity-credentials/
instance-action
instance-id
instance-type
local-hostname
local-ipv4
mac
metrics/
network/
placement/
profile
public-hostname
public-ipv4
public-keys/
reservation-id
security-groups
services/[ec2-user@ip-172-31-44-74 ~]$ curl http://169.254.169.254/latest/meta-data/hostname
ip-172-31-44-74.eu-west-1.compute.internal[ec2-user@ip-172-31-44-74 ~]$ curl http://169.254.169.254/latest/meta-data/instance-id
i-078d9f318a100da22[ec2-user@ip-172-31-44-74 ~]$ curl http://169.254.169.254/latest/meta-data/events/
maintenance/[ec2-user@ip-172-31-44-74 ~]$ 
```