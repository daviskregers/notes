---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/vpc, networking, review]
sr-due: 2022-11-25
sr-interval: 2
sr-ease: 190
---

# NAT Instances - Network Address Translation (outdated)

- Allows instances in the [[private subnet]]s to connect to the internet
- Must be launched in a [[public subnet]]
- Must disable [[AWS EC2]] flag: [[Source - Destination Check]]
- Must have [[Elastic IP]] attached to it
- [[Route Table]] must be configured to route traffic from [[private subnet]]s to [[NAT Instance]]


![](2020-01-01-16-40-26.png)

To do this, we are going to add a new [[AWS EC2]] instance with a [[NAT template]].

![](2020-01-01-16-44-56.png)

Place it in the [[public subnet]]

![](2020-01-01-16-45-28.png)

![](2020-01-01-16-48-08.png)

![](2020-01-01-16-51-46.png)

And we are going to launch a private instance in the [[private subnet]].

![](2020-01-01-16-49-07.png)

Make sure to disable the [[Source - Destination Check]] for the [[NAT]].

![](2020-01-01-16-50-27.png)

Also would be recommended that the key pair is a different from the public ones.

Then edit the routes of the Private Instance and add the [[NAT Instance]].

![](2020-01-01-16-53-38.png)

By doing this, the private instance will have an access to the internet, through the NAT instance.

## NAT Instances - Comments

- [[Amazon Linux AMI]] - preconfigured available
- Not [[highly available]] / [[resilient]] setup out of the box
- Would need to create [[Auto Scaling Group (ASG)]] in [[Multi-AZ]] + resilient [[EC2 User Data]] script
- Internet traffic bandwidth depends on [[AWS EC2]] instance performance
- Must manage [[security group]]s & rules
    - Inbound
        - Allow [[HTTP]] / [[HTTPS]] traffic coming from [[private subnet]]s
        - Allow [[SSH]] from your home network (access is provided though [[Internet Gateway & Route tables]])
    - Outbound
        - Allow [[HTTP]] / [[HTTPS]] traffic to the internet