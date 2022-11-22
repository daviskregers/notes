---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2, review]
sr-due: 2022-11-25
sr-interval: 3
sr-ease: 230
---

# EC2 for Solutions Architects

- [[AWS EC2]] instances are billed by the second, t2.micro is free tier
- On [[Linux]] / [[Mac]] we use [[SSH]], on [[Windows]] we use [[Putty]]
- [[SSH]] is on [[port]] 22, lock down the [[security group]] to your [[IP]]
- [[Timeout]] issues => [[Security Group]] issues
- Permission issues on the [[SSH key]] => run "chmod 0400"
- [[Security Group]]s can reference other [[Security Group]]s instead of [[IP range]]s (very popular exam question)
- Know the difference between [[Private IP]], [[Public IP]] and [[Elastic IP]]
- You can customise an [[AWS EC2]] instance at boot time using [[EC2 User Data]]
- Know the 4 [[EC2 Instance Launch Types]]:
- Know the basic instance types: R, C, M, I, G, T2/T3
- You can create [[EC2 AMIs]] to pre-install software on your EC2 => faster boot
- [[EC2 AMIs]] can be copied across regions and accounts
- [[EC2 Placement Groups]]