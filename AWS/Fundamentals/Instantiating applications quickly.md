---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/fundamentals]
---

# Instantiating applications quickly

- When launching a full-stack ([[AWS EC2]], [[EBS Volume]], [[AWS RDS]]), it can take time to:
    - Install applications
    - Insert initial (or recovery) data
    - Configure everything
    - Launch application
- We can take advantage of the cloud to speed that up.
- EC2 Instances
    - Use a [[Golden AMI]]: Install your applications, OS dependencies etc before hand and launch your EC2 instance from the Golden AMI.
    - Bootstrap using User Data: For dynamic configuration, use user data scripts.
    - Hybrid: mix Golden AMI and User Data (Elastic Beanstalk).
- [[AWS RDS]]:
    - Restore from snapshot: the database will have schemas and data ready.
- [[EBS Volume]]:
    - Restore from a snapshot: the disk will already be formatted and have data.