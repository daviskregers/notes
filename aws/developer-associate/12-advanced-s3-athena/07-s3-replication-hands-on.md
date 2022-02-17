# S3 Replication Hands On

1. Make sure the versioning is turned on
2. Create a new bucket, preferably into a different region, enable the versioning for it as well.

![](img/2022-02-17-06-57-30.png)

3. Under the original bucket we can go to `Management -> Replication Rules` and add one.

Here we can either enable the scope to be some specific files or all objects in the bucket.

![](img/2022-02-17-06-59-49.png)

We can select an S3 bucket in this or another account.

![](img/2022-02-17-07-00-23.png)

Finally we need an IAM role to perform this action, we can ask AWS to create one for us.

![](img/2022-02-17-07-01-14.png)

Other options include encryption, destination storage class, and replication settings.

![](img/2022-02-17-07-01-52.png)

When creating, there is an option to replicate existing objects as well.

![](img/2022-02-17-07-04-41.png)

Now, if we upload a file into the primary bucket:

![](img/2022-02-17-07-08-51.png)

After a few seconds it should show up in the replica as well:

![](img/2022-02-17-07-09-18.png)

Note: that the deletes are not replicated across the buckets.