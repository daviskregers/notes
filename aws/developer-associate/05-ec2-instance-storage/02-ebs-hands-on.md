# EBS Hands On

If we go to EC2 and inspect our instance, under the storage tab, we'll see that it has a root device with a type of EBS volume.

![](img/2021-09-15-17-09-06.png)

Also there is a section `Block devices` that will lost all attached storages. Currently we only have the root device.

![](img/2021-09-15-17-10-33.png)

We can also go to `EC2 -> Elastic Block Store -> Volumes` and create a new volume.

We are going to create a 2 GB General purpose storage in the same availability zone that our ec2 instance is located in.

![](img/2021-09-15-17-14-26.png)

Now we'll see 2 volumes in our list - one is in use (the root volume) and one that is available (the one we created just now).

![](img/2021-09-15-17-15-34.png)

We can now attach our volume to the EC2 instance by right-clicking.

![](img/2021-09-15-17-16-25.png)
![](img/2021-09-15-17-16-51.png)

Now under the instance, we'll see both of these volumes:

![](img/2021-09-15-17-17-51.png)