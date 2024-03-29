---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/storage/efs, review]
sr-due: 2022-11-25
sr-interval: 3
sr-ease: 230
---

# EFS Hands on

Before we start using [[EFS - Elastic File System]], we have to go to [[Security Group]]s and create a new [[security group]]. All the [[inbound]]/[[outbound]] rules can be left at default.

![](2019-12-30-07-49-44.png)

Next, we can go to `EFS Service`.

![](2019-12-30-07-51-02.png)

And click on `Create file system`

![](2019-12-30-07-51-22.png)

Change the default [[security group]] to the previously created one.

![](2019-12-30-07-52-41.png)

When going through, we should see that the [[EFS - Elastic File System]] is creating, it has a `File system ID` and it has 3 [[IP]]s on each specified [[Availability Zone]]s.

![](2019-12-30-07-54-36.png)

When the [[EFS instance]]s are done setup, we can go to [[AWS EC2]] and launch a new instance.

When creating it, select an [[Availability Zone]].

![](2019-12-30-07-57-23.png)

When the instance has been created, right-click on it and select `Launch more like this`.

![](2019-12-30-08-00-02.png)

Then click on `Edit Instance details` and select a different [[Availability Zone]].

![](2019-12-30-08-00-55.png)

Once that's done, we can [[SSH]] into the instances and setup the [[EFS - Elastic File System]]. The instructions for that are available at the EFS page.

![](2019-12-30-08-02-01.png)

```
sudo yum install -y amazon-efs-utils
sudo mkdir /efs
sudo mount -t efs -o tls fs-aff48164:/ /efs
```

When adding these rules, you will experience a timeout.

```
mount.nfs4: Connection reset by peer
Failed to initialize TLS tunnel for fs-aff48164
```

In order to fix this, we will need to change the settings to the Security Group by adding `inbound NFS` for the security group that the ec2 instances has.

![](2019-12-30-08-10-24.png)

Now we can mount it and test it between the instances on different [[Availability Zone]]s:

![](2019-12-30-08-13-35.png)