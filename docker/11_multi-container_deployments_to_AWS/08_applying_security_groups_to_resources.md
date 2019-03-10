# Applying security groups to resources

Now, when we created a security group, we'll need to add the resources to this group.

## Elasticache Redis

First, we can go to `Services -> Elasticache -> Redis`, select our previously created instance and click on `modify`. Then we'll modify the `VPC security groups`:

![](../../images/2019-03-10-14-12-49.png)

And apply the changes.

# RDS Postgres

Go to `Services -> RDS`, check the created instance and click on `Modify`.
Under the `Network & Security` box, we can apply a security group:

![](../../images/2019-03-10-14-15-50.png)

# Elastic Beanstalk

Go to `Services -> Elastic Beanstalk -> Multidocker-env -> Configuration -> Instances -> EC2 security groups`

![](../../images/2019-03-10-14-18-00.png)