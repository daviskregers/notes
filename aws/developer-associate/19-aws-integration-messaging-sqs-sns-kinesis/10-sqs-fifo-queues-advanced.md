# SQS FIFO Queues Advanced

## Deduplication

- De-duplication interval is 5 minutes
- Two de-duplication methods:
    - Content-based deduplication: will do a SHA-256 hash of the message body
    - Explicitly provide a Message Deduplication ID

![](2022-04-27-07-07-48.png)

## Message Grouping

- If you specify the same value of MessageGroupID in an SQS FIFO queue, you can only have one consumer, and all the messages are in order
- To get ordering at the level of a subset of messages, specify different values for MessageGroupID
    - Messages that share a common MessageGroupID will be in order within the group
    - Each Group ID can have different consumer (parallel processing)
    - Ordering across groups is not guaranteed

![](2022-04-27-07-09-31.png)

![](2022-04-27-07-09-56.png)

![](2022-04-27-07-10-20.png)