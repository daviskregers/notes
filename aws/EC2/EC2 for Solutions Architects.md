---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# EC2 for Solutions Architects

- EC2 instances are billed by the second, t2.micro is free tier
- On Linux / Mac we use SSH, on Windows we use Putty
- SSH is on port 22, lock down the security group to your IP
- Timeout issues => Security group issues
- Permission issues on the SSH key => run "chmod 0400"
- Security Groups can reference other Security Groups instead of IP ranges (very popular exam question)
- Know the difference between Private, Public and Elastic IP
- You can customize an EC2 instance at boot time using EC2 User Data
- Know the 4 EC2 launch modes:
    - On demand
    - Reserved
    - Spot Instances
    - Dedicated Hosts
- Know the basic instance types: R, C, M, I, G, T2/T3
- You can create AMIs to pre-install software on your EC2 => faster boot
- AMI can be copied accross regions and accounts
- EC2 instances can be started in placement groups:
    - Cluster
    - Spread
    - Parition