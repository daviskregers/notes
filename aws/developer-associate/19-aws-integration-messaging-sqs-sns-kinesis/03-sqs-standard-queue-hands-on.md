# SQS Standard Queue Hands On

We are going to create a new queue

![](img/2022-04-27-06-32-00.png)

![](img/2022-04-27-06-32-49.png)

![](img/2022-04-27-06-33-05.png)

![](img/2022-04-27-06-34-10.png)

Now the queue is created, we can send and receive messages from it.
Click on Send and Receive messages when opening up the queue.

![](img/2022-04-27-06-35-39.png)

![](img/2022-04-27-06-36-08.png)

![](img/2022-04-27-06-36-25.png)

![](img/2022-04-27-06-36-36.png)

Each time you poll, the receive count for the message will increase, but it will still persist in the queue. When you are done with the message - delete it.

You can also purge the queue - it will remove all the messages in the queue. But that might not be a good idea in production.

