# Amazon SQS - FIFO Queue

- FIFO - First In First Out (ordering messages in the queue)

![](img/2022-04-27-07-04-42.png)

- Limited throughput: 300msg/s without matching, 3000 msg/s with batching
- Exactly-once send capability (by removing duplicates)
- Messages are processed in order by the consumer

You have to end the queue name with `.fifo`.

![](img/2022-04-27-07-05-35.png)


