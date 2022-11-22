---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2, review]
sr-due: 2022-12-04
sr-interval: 17
sr-ease: 250
---

## Launching an EC2 Instance running Linux

- We'll be launching our first [[virtual server]] using the [[AWS Console]]
- We'll get a first high level approach to the various parameters
- We'll learn on how to start / stop / terminate our instances

In order to do this, we go to the [[AWS console]] and launch `EC2`. Make sure that you are in the region you want to set everything up in.

![](../../../images/2019-11-22-10-50-30.png)

The first thing we want to do is to launch an instance. 

![](../../../images/2019-11-22-10-51-20.png)

We will given a list of [[distributions]] available, but it would be recommended to use the `Amazon Linux 2` since it is optimized for use with AWS and it has free tier available.

![](../../../images/2019-11-22-10-52-43.png)

Then we can choose an instance type, which basically describes on how much [[vCPU]]s, [[RAM]], [[storage]] we need.

![](../../../images/2019-11-22-10-53-12.png)

We'll choose the `t2.micro` since it is free tier eligible and click on the `Next: Configure Instance Details`.

![](../../../images/2019-11-22-10-58-27.png)

Here will be various parameters that we can set up - instance count, [[networking]], [[IAM Role]]s etc.

When clicking on next, we will be asked about the storage.

![](../../../images/2019-11-22-11-00-20.png)

The next section is for tags, which are key-value pairs to classify instances.

![](../../../images/2019-11-22-11-02-13.png)

The name tag is quite important because it will show in the UI.

The next step is Security Groups, it is basically a firewall around our instance.

![](../../../images/2019-11-22-11-04-12.png)

Now we can review the instance creation task

![](../../../images/2019-11-22-11-04-56.png)

The last step, when we click on launch, is to create a key pair which is used to log into the instance. 

![](../../../images/2019-11-22-11-06-07.png)

Click on `Download Key Pair` and `Launch Instances`.

Then we should see the instance.

![](../../../images/2019-11-22-11-07-30.png)

Once it's created, it will show a state of `Running`. You can stop or terminate it by right clicking onto it.

![](../../../images/2019-11-22-11-08-54.png)
