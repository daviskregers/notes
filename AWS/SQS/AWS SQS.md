---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/sqs, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# AWS SQS

## AWS SQS - Standard Queue

- Oldest offering (over 10 years old)
- Fully managed
- Scales from 1 message per second to 10,000s per second
- Default retention of messages: 4 days, maximum of 14 days
- No limit to how many messages can be in the queue
- Low latency (< 10 ms on publish and receive)
- Horizontal scaling in terms of number of consumers
- Can have duplicate messages (at least once delivery, occasionally)
- Can have out of order messages (best effort ordering)
- Limitation of 256KB per message sent

## AWS SQS - Delay Queue

- Delay a message (consumers don't see it immediately) up to 15 minutes
- Default is 0 seconds (message is available right away)
- Can set a default at queue level
- Can override the default using the DelaySeconds parameter

## SQS - Producting messages

- Define Body
- Add message attributes (metadata, optional)
- Provide Delay Delivery (optional)
- Send to SQS
- Get back
    - Message identifier
    - MD5 has of the body

## SQS - Consuming Messages

- Poll SQS for messages (receive up to 10 messages at a time)
- Process the message within the visibility timeout
- Delete the message using the message ID & receipt handle

## SQS - Visibility Timeout

- When a consumer polls a message from a queue, the message is "invisible"'to other consumers for a defined period. The Visibility Timeout.
- You can set between 0 seconds and 12 hours (default to 30 seconds).
    - If you set too high (15 minutes) and consumer fails to process the message, you must wait a long time before processing the message again.
    - If you set too low (30 seconds) and consumer needs time to process the message (2 minutes), another consumer will receive the message will be processed more than once.
- ChangeMessageVisibility API to change the visibility while processing a message.
- DeleteMessage API to tell SQS the message was successfully procesed.

## AWS SQS - Dead Letter Queue

- If a consumer fails to process a message within the visibility timeout the message goes back to the queue.
- We can set a threshold of how many times a message cen go back to the queue - it's called a "redrive policy"
- After the threshold is exceeded, the message goes into a dead letter queue (DLQ)
- We have to create a DLQ first and then designate it dead letter queue
- Make sure to process the messages in the DLQ before they expire.

## AWS SQS - Long Polling

- When a consumer requests message from the queue, it can optionally wait for messages to arrive if there are none in the queue.
- This is called long polling
- LongPolling decreases the number of API calls made to sqs while increasing the efficency and latency of your application.
- The wait time can be between 1 to 20 sec (20 sec preferable)
- Long Polling is preferable to short polling
- Long polling can be enabled at the queue level or at the API level using WaitTimeSeconds

## SQS Message Consumption flow diagram

![](2019-12-31-10-06-22.png)

## AWS SQS - FIFO Queue

- Newer offering (First In - First Out) - not available in all regions
- Name of the queue must end in .fifo
- Lower throughput (up to 3,000 per second with batching, 300/s without)
- Messages are processed in order by the consumer
- Messages are sent exactly once
- No per message delay (only per queue delay)
- Ability to do content based de-duplication
- 5 minute interval de-duplication using "Duplication ID"
- Message groups
    - Possibility to group messages for FIFO ordering using "Message GroupID"
    - Only one worker can be assigned per messsage group so that messages are processed in order
    - Message group is just an extra tag on the message

## Hands on

We can access `SQS` in AWS Console.

![](2019-12-31-10-11-39.png)

![](2019-12-31-10-12-39.png)

Click on `Configure Queue`.

![](2019-12-31-10-14-32.png)

Now the queue should be visibl and there will be multiple options for it:

![](2019-12-31-10-15-51.png)

We are going to send a message.

![](2019-12-31-10-16-32.png)

![](2019-12-31-10-16-59.png)

![](2019-12-31-10-17-41.png)

![](2019-12-31-10-18-14.png)

![](2019-12-31-10-19-35.png)