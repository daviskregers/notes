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

## Troubleshooting

- There's a connection timeout.

    This is a security group issue. Any timeout (not just for SSH) is related to security groups or a firewall. Ensure your security group looks like this and correctly assigned to your EC2 instance.

- There's still a connection timeout issue

    If your security group is properly configured as above, and you still have connection timeout issues, then that means a corporate firewall or a personal firewall is blocking the connection. Please use EC2 Instance Connect as described in the next lecture.

- SSH does not work on Windows

    If it says: ssh command not found, that means you have to use Putty

    Follow again the video. If things don't work, please use EC2 Instance Connect as described in the next lecture

- There's a connection refused

    This means the instance is reachable, but no SSH utility is running on the instance

    Try to restart the instance

    If it doesn't work, terminate the instance and create a new one. Make sure you're using Amazon Linux 2

- Permission denied (publickey,gssapi-keyex,gssapi-with-mic)

    This means either two things:

    You are using the wrong security key or not using a security key. Please look at your EC2 instance configuration to make sure you have assigned the correct key to it.

    You are using the wrong user. Make sure you have started an Amazon Linux 2 EC2 instance, and make sure you're using the user ec2-user. This is something you specify when doing ec2-user@<public-ip> (ex: ec2-user@35.180.242.162) in your SSH command or your Putty configuration