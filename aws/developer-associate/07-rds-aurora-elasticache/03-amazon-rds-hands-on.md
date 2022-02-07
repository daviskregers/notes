# Amazon RDS Hands On

We can open up the RDS service in AWS

![](img/2022-02-07-17-40-00.png)

And go to the `databases` secion and click on create database

![](img/2022-02-07-17-40-31.png)

There will we have different options:

- We can choose the creation method:

![](img/2022-02-07-17-44-40.png)

We are going to choose the standard one. In it the first choice to make is to pick a database engine:

- Amazon Aurora
- MySQL
- MariaDB
- PostgreSQL
- Oracle
- Microsoft SQL Server

![](img/2022-02-07-17-45-53.png)

We are going to select MySQL and select the latest version.

![](img/2022-02-07-17-46-59.png)

Next we can choose between some templates that will be pre-filling the following configurations with best suited values. We are going to use the Production one but modify it to be compliant with free tier.

![](img/2022-02-07-17-48-13.png)

Next we can choose our availability and durability settings. For free tier pick Single DB Instance.

![](img/2022-02-07-17-49-51.png)

In the settings section we can set the identifier, username and password.

![](img/2022-02-07-17-50-05.png)

Next we can choose the instance types. For free tier use db.t2.micro
![](img/2022-02-07-17-50-19.png)

Next we can choose the storage type. For free tier use gp2. You can also set the allocated storage and enable storage autoscaling.

![](img/2022-02-07-17-50-29.png)

In the connectivity section we can choose the VPC the database will be placed into. Whether the database is publicly available. The security groups and port under additional configuration.

![](img/2022-02-07-17-50-54.png)


We can also choose the authentication methods.

![](img/2022-02-07-17-51-16.png)

Under the additional configuration we can:

Set the initial database name, parameter groups, option groups.

![](img/2022-02-07-18-01-22.png)

Configure backups

![](img/2022-02-07-18-01-46.png)

Configure encryption

![](img/2022-02-07-18-02-25.png)

Enable performance insights

![](img/2022-02-07-18-02-56.png)

Configure retention period

![](img/2022-02-07-18-03-21.png)

Configure monitoring

![](img/2022-02-07-18-03-45.png)


Configure maintenance and toggle deletion protection

![](img/2022-02-07-18-04-13.png)

---

Once done setting up, we can click on create the database and it will show up on the databases section wth a status of `creating`.

![](2022-02-07-18-08-19.png)

It can take a few minutes for it to be ready.

Once it's done, we can open it up and see the connectivity tab which will list the endpoint and the port t connect to:

![](img/2022-02-07-18-13-29.png)

In the next tab we can see monitoring

![](2022-02-07-18-14-17.png)

There are also several actions we can take:

- Create a read replica for larger read capacity
- Take a snapshot - create a backup of the database which you can spin up elsewhere.
- Restore to point in time
- Migrate snapshot - in a different region for example
- Stop
- Reboot
- Delete

![](img/2022-02-07-18-15-14.png)
![](img/2022-02-07-18-17-12.png)