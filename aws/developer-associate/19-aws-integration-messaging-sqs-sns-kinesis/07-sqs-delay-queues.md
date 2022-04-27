# SQS - Delay Queue

- Delay a message (consumers don't see it immediately) up to 15 minutes
- Default is 0 seconds (message is available right away)
- Can set a default at queue level
- Can override the default on send using the *DelaySeconds* parameter

![](img/2022-04-27-06-57-38.png)

![](img/2022-04-27-06-57-57.png)

![](img/2022-04-27-06-58-17.png)