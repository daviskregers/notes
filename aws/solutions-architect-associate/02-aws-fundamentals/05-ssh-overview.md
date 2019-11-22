# SSH Overview

We can use SSH to connect to the newly created instance. It works for Mac, Linux and Windows 10. If you're on windows below version 10, you can use `Putty` to ssh into the instance.

Alternatively, you can use `EC2 Instance Connect` to do the same thing via the `AWS Console`.

## SSH from Linux or Mac

Get the Public IP of the intance you want to connect to:

![](../../../images/2019-11-22-11-12-48.png)

Open up a terminal on your OS. Move your key pair file you downloaded when creating the instance.

```bash
➜  notes git:(master) ✗ sudo chmod 0400 ~/Downloads/EC2Tutorial.pem
[sudo] password for davis: 
er@52.211.212.92
The authenticity of host '52.211.212.92 (52.211.212.92)' can't be established.
ECDSA key fingerprint is SHA256:8os5YxNJ1iInCADO07oMntsT/8g+kSsK4z2R1xQvzZU.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '52.211.212.92' (ECDSA) to the list of known hosts.

       __|  __|_  )
       _|  (     /   Amazon Linux 2 AMI
      ___|\___|___|

https://aws.amazon.com/amazon-linux-2/
5 package(s) needed for security, out of 13 available
Run "sudo yum update" to apply all updates.
[ec2-user@ip-172-31-41-154 ~]$ pwd
/home/ec2-user
[ec2-user@ip-172-31-41-154 ~]$ 
```

## SSH Using Windows

Download [Putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) and install it.

We can open up `Putty Key Generator` to convert the keypair we downloaded previously from `.pem` to `.ppk`.

Click on `Load private key`, open up the keypair. Load it and click on `Save private key`.

![](../../../images/2019-11-22-11-18-35.png)

Then we can open up `PuTTY` and enter the username and IP address of our EC2 machine, save it.

![](../../../images/2019-11-22-11-20-19.png)

Then go to `Connection -> SSH -> Auth`, where we can specify the private key.

![](../../../images/2019-11-22-11-21-29.png)

## SSH using Windows 10

You can use `PowerShell` or `cmd`. Type in `ssh` and it should be available. If it's not, you will need to use the `PuTTY` route.

![](../../../images/2019-11-22-11-23-08.png)

If it throws an error regarding keypair permissions, open up the properties of the file, go to the `Security tab -> Advanced`, change the owner to yourself, remove any other users. If you cannot do that, disable the Inheritance.

![](../../../images/2019-11-22-11-25-22.png)

## EC2 Instance Connect

While viewing the instances in our EC2 dashboard, we can select an instance and click on `Connect` button.

![](../../../images/2019-11-22-11-28-33.png)

![](../../../images/2019-11-22-11-29-06.png)

![](../../../images/2019-11-22-11-29-33.png)

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