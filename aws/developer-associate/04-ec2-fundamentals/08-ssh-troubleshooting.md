# SSH troubleshooting

## 1. There's a connection timeout

This is a security group issue. Any timeout (not just for SSH) is related to security groups or a firewall.

## 2. There's still a connection timeout issue

If your security group is properly configured as above, and you still have connection timeout issues, then that means a corporate firewall or a personal firewall is blocking the connection. Use the EC2 Instance Connect.

## 3. SSH does not work on Windows

- If it says `ssh command not found`, that means that you have to use Putty.
- If that doesn't work - use the EC2 instance connect.

## 4. There's a connection refused

This means that the instance is reachable, but no SSH utility is running on the instance

- Try to restart the instance
- If it doesn't work, terminate the instance and create a new one. Make sure you're using Amazon Linux 2

## 5. Permission denied (publickey, gssapi-keyex,gssapi-with-mic)

This means either two things:
- You are using wrong security key or not using a security key.
- You are using the wrong user. Make sure you have started an Amazon Linux 2 EC2 instance, and make sure you're using the user ec2-user.