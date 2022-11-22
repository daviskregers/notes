---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/ami, review]
sr-due: 2022-12-14
sr-interval: 23
sr-ease: 250
---

# EC2 AMIs

As we previously saw, AWS comes with base images such as:
- [[Ubuntu]]
- [[Fedora]]
- [[RedHat]]
- [[Windows]]
- etc

These images can be customised at runtime using [[EC2 User Data]]

But, you can create your own image, which can be done with an `AMI`.

Using custom built AMI can provide with following advantages:
- Pre-installed packages needed
- Faster boot time (no need for [[EC2 User Data]] at boot time)
- Machine comes configured with monitoring / enterprise software
- Security concerns - control over the machines in the network
- Control of maintenance and updates of AMIs over time
- [[Active Directory Integration]] out of the box
- Installing your app ahead of time (for faster deploys when auto-scaling)
- Using someone else's [[EC2 AMIs]] that is optimised for running an app, DB, etc..

**AMI are built for a specific AWS region!**

Using public AMIs
- You can leverage AMIs from other people
- You can also pay for other people's AMI by the hour
    - These people have optimised the software
    - The machine is easy to run and configure
    - You basically rent "expertise"'from the AMI creator
- AMI can be found and published on the Amazon Marketplace

**Warning**
- Do not use an AMI you don't trust
- Some AMIs might come with malware or may not be secure for your enterprise

![[ AMI Storage ]]

![[AMI Pricing]]

[[ EC2 AMI Hands On]]
[[Cross Account AMI Copy]]
