# Section introduction

- So far, we've interacted with services manually and they exposed standard information for clients
    - EC2 exposes a standard linux machine we can use any way we want
    - RDS exposes a standard database we can connect to using a URL
    - ElastiCache exposes a cache URL we can connect to using a URL
    - ASG / ELB are automated and we don't have to program ainst them
    - Route53 was setup manual
- Developing against AWS has two components
    - How to perform interactions with AWS without using the Online Console?
    - How to interact with AWS Proprietary services? S3, DynamoDB etc...
- Developing and performing AWS tasks against AWS can be done in several ways:
    - Using the AWS CLI on our local computer
    - Using the AWS CLI on our EC2 machines
    - Using the AWS SDK on our local computer
    - Using the AWS SDK on our EC2 machines
    - Using the AWS Instance Metadata Service for EC2