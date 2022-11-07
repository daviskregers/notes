# Aurora hands on

Once again, we are going to `RDS` service in AWS console and choosing `create database`. This time we are going to select `Aurora` engine.

- Select version and location
- Choose a template
- Setup identifier and credentials
- Choose instance size
- Availability & durability
- Connectivity
- Database authentication

![](2019-12-30-09-28-28.png)

When done, it will create a master and a read replica. If needed, you can manually add more readers or create an auto scaling policy.

![](2019-12-30-09-31-16.png)

![](2019-12-30-09-31-41.png)