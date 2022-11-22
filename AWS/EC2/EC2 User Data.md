---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2, review]
sr-due: 2022-12-16
sr-interval: 24
sr-ease: 250
---

# EC2 User Data

- It is possible to bootstrap our instances using an EC2 User data script
- Bootstrapping means launching commands when a machine starts
- That script is only run once at the instance first start
- EC2 user data is used to automate boot tasks such as:
    - Installing updates
    - Installing software
    - Downloading common files from the internet
    - Anything you can think of
- The EC2 User Data Script runs with the root user

We want to make sure that this EC2 instance has an Apache HTTP server installed on it - to display a simple web page

For it we are going to write a user-data script.

This script will be executed at the first boot of the instance.

## Hands on

First we are going to terminate the instance we made previously.

![](../../../images/2019-11-22-12-11-21.png)

Then launch a new instance. We are going to follow the same steps as for the [previous instance creation process](05-ec2-introduction.md), but when we are in the `Configure Instance` section, there is a `Advanced Details` section with user data settings.

![](../../../images/2019-11-22-12-13-34.png)

We will input it as text.

```bash
#!/bin/bash
yum update -y
yum install -y httpd.x86_64
systemctl start httpd.service
systemctl enable httpd.service
echo "Hello World from $(hostname -f)" > /var/www/html/index.html
```

![](../../../images/2019-11-22-12-15-22.png)

For security group, this time we are going to use `An existing security group`.

![](../../../images/2019-11-22-12-16-38.png)

For keypair, we can reuse the previously created one.

![](../../../images/2019-11-22-12-17-24.png)

Once it has launched, we should be able to grab the Public IP and see the created web server publicly available.

![](../../../images/2019-11-22-12-18-54.png)

![](../../../images/2019-11-22-12-19-29.png)