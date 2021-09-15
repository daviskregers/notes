# EBS Snapshots hands on

When working with volumes, there is an option to create a snapshot for it.

![](img/2021-09-15-17-21-56.png)
![](img/2021-09-15-17-22-26.png)

To verify that the snapshot was created we can go to `EC2 -> Elastic Block Storage -> Snapshots`

![](img/2021-09-15-17-23-22.png)

Now when it's available we can do multiple things with it:

![](img/2021-09-15-17-24-56.png)


- copy it across regions:

![](img/2021-09-15-17-24-17.png)

- create a volume from it (also in a different AZ)

![](img/2021-09-15-17-27-05.png)