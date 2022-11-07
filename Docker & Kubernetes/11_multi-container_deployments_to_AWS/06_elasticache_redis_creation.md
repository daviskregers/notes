# Elasticache redis creation

To create `Elasticache Redis` we'll go to `Services -> Elasticache -> Redis` and click on `Create`.

We'll leave the `Cluster mode` disabled and set up the name and change the `note type` since the default one is quite expensive. Set `Number of Replicas` to 0.

![](../../images/2019-03-10-13-53-26.png)

Also, we'll make a `subnet` called `redis-group` and target it to the default VPC, check all the subnets.

Now the instance is creating:

![](../../images/2019-03-10-13-56-12.png)

After some time, it will change status as available:

![](../../images/2019-03-10-13-59-54.png)