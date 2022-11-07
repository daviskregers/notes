# DynamoDB Basics - Hands On

We can open up the DynamoDB service in AWS Console and create a new table.

At first we need to fill out the table name and a primary key (optionally the sort key as well).

![](2022-05-17-06-42-05.png)

Next, we can choose either the default settings or to customize them, like table class - standard or infrequent access.

![](2022-05-17-06-43-17.png)

Next, we have a capacity calculator, at which we will look into later.

![](2022-05-17-06-44-10.png)

Next, we can select the On-demand or Provisioned capacity mode. Note that the Provisioned is in the free-tier.

![](2022-05-17-06-45-37.png)

Next, we can set the read and write capacity. For free tier we can turn off the auto scaling and set both to 2 provisioned capacity units.

![](2022-05-17-06-46-50.png)

Next, we can set up the secondary indexes. We are going to look into that later.

![](2022-05-17-06-47-28.png)

Finally, we can set up the encryption.

![](2022-05-17-06-48-08.png)

---

Our table has now been created.

![](2022-05-17-06-49-00.png)

We can open it up and have a lot of information about it.

![](2022-05-17-06-49-36.png)

If we click on the View items, we can scan or query them.

![](2022-05-17-06-50-25.png)

We are going to create an item - there's a button for that.

It will open up a form where you can set the partition key and add additional fields. Optionally, you can choose to add the item in JSON format.

![](2022-05-17-06-51-40.png)

![](2022-05-17-06-51-57.png)

![](2022-05-17-06-53-04.png)

In DynamoDB it is fine that most of the columns are left empty, the only mandatory field is the primary key.

---

Next, we can set up another table UserPosts, where the primary key is the user_id and the sort key is post timestamp.

![](2022-05-17-06-54-44.png)

![](2022-05-17-06-55-03.png)

![](2022-05-17-06-55-25.png)

![](2022-05-17-06-55-59.png)