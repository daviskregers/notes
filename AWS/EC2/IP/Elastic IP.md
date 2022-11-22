---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/ip, review]
sr-due: 2022-12-13
sr-interval: 21
sr-ease: 250
---

## Elastic IP

- When you stop and then start an [[AWS EC2]] instance, it can change it's [[Public IP]]
- If you need to have a fixed public IP for your instance, you need an Elastic IP
- An elastic IP is a public [[IPv4]] IP you own as long as you don't delete it
- You can attach to it one instance at a time
- With an Elastic IP address, you can mask the failure of an instance or software by rapidly remapping the address to another instance on your account
- You can only have 5 Elastic IP in your account (you can ask AWS to increase that)
- Overall, try to avoid using Elastic IP
	- They often reflect poor [[architectural decisions]]
	- Instead, use a random public IP and register a DNS name to it
	- Or use a Load Balancer and don't use a public IP at all