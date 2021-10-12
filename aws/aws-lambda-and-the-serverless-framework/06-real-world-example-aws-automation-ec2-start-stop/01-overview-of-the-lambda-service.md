# Overview of EC2 start & stop service

We are going to make a service that leverages CloudWatch schedule and every day at 9am start an EC2 instance. Every day at 5pm it will stop it.

## What we'll use

- Python runtime
- CloudWatch events
- IAM Permissions to stop and start ec2 instances
- Function timeouts and memory