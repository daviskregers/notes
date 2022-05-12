# Lambda Destinations Hands On

We can add a destination for a lambda

![](img/2022-05-12-08-19-08.png)

We are going to create 2 new queues - one for successful invocations and one for failures. Then we are going to add them as destinations.

![](img/2022-05-12-08-20-51.png)

![](img/2022-05-12-08-21-20.png)

![](img/2022-05-12-08-21-58.png)

Now when executing the lambda, we will see a message in the queue:

![](img/2022-05-12-08-23-03.png)