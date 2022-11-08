---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/ip, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# Private vs Public vs Elastic IP

![[Public IP]]

![[Private IP]]

![[Elastic IP]]

By default, your EC2 machine comes with:
- A private IP for internal AWS network
- A public IP for the internet

When we are doing ssh into our ec2 machines:
- We can't use a private IP, because we are not in the same network
- We can only use the public IP

If your machine is stopped and then started, the public IP can change

When viewing the EC2 instance, we can see these IP addresses:

![](../../../images/2019-11-22-11-57-46.png)

You can also visit the `Elastic IPs` section and allocate new Elastic IP adresses.

![](../../../images/2019-11-22-11-58-28.png)

![](../../../images/2019-11-22-11-58-44.png)

Once it's created, we can associate it with an instance.

![](../../../images/2019-11-22-11-59-31.png)