# AMI Hands on

In order to play with AMI we are going to create a new EC2 instance. Will all the default settings except for the `User data` field.

In it we are going to input the following:

```bash
#!/bin/bash
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httd
```

Once the instance is up and running, we can open it's public IP in a browser.

![](2021-09-15-17-34-22.png)

Now we are going to create an AMI from it.

![](2021-09-15-17-35-18.png)

![](2021-09-15-17-36-16.png)

We'll have to wait some time until the AMI becomes available. We can check that in `EC2 -> Images -> AMIs`.

![](2021-09-15-17-37-25.png)

Now we can go to `Launch instances -> My AMIs` and select our AMI. Then in the user data we input this:

```bash
#!/bin/bash
echo "<h1>Hello World from $(hostname -f)</h1>" > /var/www/html/index.html
```

And once it's up, we can visit in the browser and see the custom hello text.