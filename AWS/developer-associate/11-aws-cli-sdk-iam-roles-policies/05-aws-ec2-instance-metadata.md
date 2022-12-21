# AWS EC2 Instance Metadata

- AWS EC2 Instance Metadata is a powerful but on of the least known features to developers
- It allows AWS EC2 instances to learn about themselves without using an IAM Role for that purpose.
- The url is http://169.254.169.254/latest/meta-data
- You can retrieve the IAM Role name from the metadata, but you CANNOT retrieve the IAM Policy
- Metadata - info about the EC2 instance
- Userdata - launch script of the EC2 instance

```console
$ curl http://169.254.169.254/latest/meta-data/instance-id
i-05adcce6933809eda
$ curl http://169.254.169.254/latest/meta-data/local-ipv4
172.31.3.136
$ curl http://169.254.169.254/latest/meta-data/iam/security-credentials
MyFirstEC2Role
$ curl http://169.254.169.254/latest/meta-data/iam/security-credentials/MyFirstEC2Role
{
    "Code" : "Success",
    "LastUpdated" : "...",
    "Type" : "AWS-HMAC",
    "AccessKeyId" : "...",
    "SecretAccessKey" : "...",
    "Token" : "...",
    "Expiration" : "..."
}
```