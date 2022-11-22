---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/ssh, review]
sr-due: 2023-01-14
sr-interval: 53
sr-ease: 270
---

## [[SSH]] using [[Windows]] 10

You can use [[PowerShell]] or [[cmd]]. Type in `ssh` and it should be available. If it's not, you will need to use the [[PuTTY]] route.

![](../../../images/2019-11-22-11-23-08.png)

If it throws an error regarding [[keypair permissions]], open up the properties of the file, go to the `Security tab -> Advanced`, change the owner to yourself, remove any other users. If you cannot do that, disable the Inheritance.

![](../../../images/2019-11-22-11-25-22.png)
