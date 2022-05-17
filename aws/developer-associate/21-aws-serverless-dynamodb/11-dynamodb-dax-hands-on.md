# DynamoDB DAX - Hands On

In DynamoDB Console, on the left side there is DAX available. It's not in the free tier so it will cost money.

![](img/2022-05-17-07-57-22.png)

![](img/2022-05-17-07-57-50.png)

You can select the node family.

![](img/2022-05-17-07-58-40.png)

![](img/2022-05-17-07-59-04.png)

![](img/2022-05-17-07-59-23.png)

---

![](img/2022-05-17-07-59-59.png)

![](img/2022-05-17-08-00-12.png)

![](img/2022-05-17-08-00-23.png)

![](img/2022-05-17-08-00-38.png)

---

![](img/2022-05-17-08-00-59.png)

![](img/2022-05-17-08-01-13.png)

![](img/2022-05-17-08-01-26.png)

---

In the 4th step we can choose the parameter group.

![](img/2022-05-17-08-02-23.png)

In them we can specify the Item TTL and Query TTL.

![](img/2022-05-17-08-02-59.png)

The defaults are both 5 minutes:

![](img/2022-05-17-08-03-22.png)

We can also choose the maintenence window:

![](img/2022-05-17-08-03-53.png)

---

Once the cluster is created, it will provide a cluster endpoint. This is the endpoint our applications should leverage.

![](img/2022-05-17-08-04-37.png)

