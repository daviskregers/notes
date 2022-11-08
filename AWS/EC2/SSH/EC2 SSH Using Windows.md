---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/ssh, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

## SSH Using Windows

Download [Putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) and install it.

We can open up `Putty Key Generator` to convert the keypair we downloaded previously from `.pem` to `.ppk`.

Click on `Load private key`, open up the keypair. Load it and click on `Save private key`.

![](../../../images/2019-11-22-11-18-35.png)

Then we can open up `PuTTY` and enter the username and IP address of our EC2 machine, save it.

![](../../../images/2019-11-22-11-20-19.png)

Then go to `Connection -> SSH -> Auth`, where we can specify the private key.

![](../../../images/2019-11-22-11-21-29.png)
