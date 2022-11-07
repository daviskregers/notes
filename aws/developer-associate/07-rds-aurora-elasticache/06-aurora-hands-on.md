# Aurora Hands On

Lets create an Aurora Database

![](2022-02-08-05-49-35.png)

We have 2 editions available - the MySQL compatible version or PostgreSQL compatible version.

Also, we can choose the capacity to be either provisioned or serverless.
For the provisioned capacity we can also choose the replication.

Also, we have multiple versions available.

![](2022-02-08-05-52-45.png)

In the filters section we can filter out versions that support different features like span across multiple regions and parallel queries.

![](2022-02-08-05-53-54.png)

For templates we have either production or development. No free tier is available.

![](2022-02-08-05-55-08.png)

The other features are basically same as any other RDS.

When spun up it will create a writer and reader instance - different endpoints for writes and reads.

![](2022-02-08-05-56-58.png)

The aurora will have multiple actions:

![](2022-02-08-05-58-19.png)

- Add readers (add reading capacity)
- Create cross-region read replica
- Restore to point in time
- Add replica auto scaling
    - We can create an autoscaling rule based on CPU or connections that will auto scale read replicas.
- Add AWS Region
    - Enable Aurora to be global