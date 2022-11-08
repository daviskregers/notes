---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/ami, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

## Hands on

We are going to use a fresh EC2 instance and ssh into it.

![](../../../images/2019-11-22-13-02-45.png)

```bash
➜  notes git:(master) ✗ ssh -i ~/Downloads/EC2Tutorial.pem ec2-user@63.35.203.134
The authenticity of host '63.35.203.134 (63.35.203.134)' can't be established.
ECDSA key fingerprint is SHA256:IRLAu1mhR88VLPx7js5V1kxaFHlg6TtNNVDSWpZKz5c.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '63.35.203.134' (ECDSA) to the list of known hosts.

       __|  __|_  )
       _|  (     /   Amazon Linux 2 AMI
      ___|\___|___|

https://aws.amazon.com/amazon-linux-2/
5 package(s) needed for security, out of 13 available
Run "sudo yum update" to apply all updates.
[ec2-user@ip-172-31-34-217 ~]$ 
[ec2-user@ip-172-31-34-217 ~]$ sudo su
[root@ip-172-31-34-217 ec2-user]# yum update -y
[root@ip-172-31-34-217 ec2-user]# yum install -y httpd
[root@ip-172-31-34-217 ec2-user]# systemctl enable httpd
Created symlink from /etc/systemd/system/multi-user.target.wants/httpd.service to /usr/lib/systemd/system/httpd.service.
[root@ip-172-31-34-217 ec2-user]# systemctl start httpd
[root@ip-172-31-34-217 ec2-user]# echo "Hello World $(hostname -f)" > /var/www/html/index.html
[root@ip-172-31-34-217 ec2-user]# curl localhost:80
Hello World ip-172-31-34-217.eu-west-1.compute.internal
```

Visit the public IP from a browser:

![](../../../images/2019-11-22-13-06-41.png)

Now we can create an image from the instance by doing the following:

![](../../../images/2019-11-22-13-07-31.png)

![](../../../images/2019-11-22-13-08-29.png)

![](../../../images/2019-11-22-13-08-47.png)

Now we can go to AMIs section and see the image.

![](../../../images/2019-11-22-13-09-36.png)

When it's complete, we can do multiple things with it:

![](../../../images/2019-11-22-13-10-24.png)


We'll click on launch and it will take us through a new instance creation process.

![](../../../images/2019-11-22-13-11-58.png)

Once it's online, we can visit it in browser:

![](../../../images/2019-11-22-13-12-41.png)
