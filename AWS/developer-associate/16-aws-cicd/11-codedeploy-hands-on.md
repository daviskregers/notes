# CodeDeploy Hands On

Before we start using CodeDeploy we need to create 2 new IAM roles:

**A service role**

When creating a role, we can choose an AWS Service as CodeDeploy and it will allow us to choose common use cases:

![](2022-04-21-09-24-35.png)

![](2022-04-21-09-25-16.png)

![](2022-04-21-09-25-36.png)

**EC2 Service Role**

Our EC2 instance must be able to pull the data from S3, so we need to add a role for that as well.

`AmazonS3ReadOnlyAccess` permission is sufficient for that role.

---

Now we can create an CodeDeploy application.

![](2022-04-21-09-27-32.png)

Then we can create an EC2 instance we can deploy to. Make sure it has the EC2 Service role.

![](2022-04-21-09-28-50.png)

We'll also allow access from port 80.

![](2022-04-21-09-29-49.png)

Now we can ssh into the instance and run following commands:

```console
$ sudo yum update
$ sudo yum install ruby
$ wget https://aws-codedeploy-eu-west-3.s3.eu-west-3.amazonaws.com/latest/install
$ chmod +x ./install
$ sudo ./install auto
$ sudo service codedeploy-agent status
```

---

Once the EC2 is set up we need to create a deployment group in the CodeDeploy application. Their basically a set of EC2 instances, for example, that you are going to deploy to. Like dev instances, production instances etc.

We can attach tags to our instances:

![](2022-04-21-09-33-08.png)

Now we fill in the deployment group form:

![](2022-04-21-09-33-51.png)

![](2022-04-21-09-34-24.png)

![](2022-04-21-09-35-01.png)

![](2022-04-21-09-35-14.png)

![](2022-04-21-09-35-29.png)

![](2022-04-21-09-35-38.png)

![](2022-04-21-09-35-48.png)

![](2022-04-21-09-36-02.png)

---

Now we can create a new deployment.

![](2022-04-21-09-36-38.png)

![](2022-04-21-09-37-36.png)

We can create a new S3 bucket and modify the buildspec.yml to upload the files to that S3 bucket.

![](2022-04-21-09-38-39.png)