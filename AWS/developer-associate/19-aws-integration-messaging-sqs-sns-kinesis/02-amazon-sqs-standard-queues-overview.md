# Amazon SQS Standard Queues Overview

![](2022-04-27-06-22-11.png)

## Amazon SQS - Standard Queue

- Oldest offering (over 10 years old)
- Fully managed service, used to decouple applications

- Attributes:
    - Unlimited throughput, unlimited number of messages in queue
    - Default retention of messages: 4 days, maximum 14 days
    - Low latency (<10 ms on publish and receive)
    - Limitation of 256KB per message sent
- Can have duplicate messages (at least once delivery, occasionally)
- Can have out of order messages (best effort ordering)

## Producing Messages

- Produced to SQS using the SDK (SendMessage API)
- The message is persisted in SQS until a consumer deletes it
- Message retention: 4 days, maximum 14 days
- Example: send an order to be processed
    - Order ID
    - Customer ID
    - Any attributes you want

- SQS standard: unlimited throughput
- Message up to 256KB

## Consuming Messages

- Consumers (running on EC2 instances, servers or AWS Lambda)
- Poll SQS for messages (receive up to 10 messages at a time)
- Process the messages (example: insert the message into an RDS database)
- Delete the messages using the DeleteMessage API

![](2022-04-27-06-27-07.png)

## Multiple EC2 Instances Consumers

- Consumers receive and process messages in parallel
- At least once delivery
- Best-effort message ordering
- Consumers delete messages after processing them
- We can scale consumers horizontally to improve throughput of processing

![](2022-04-27-06-28-15.png)

## SQS with Auto Scaling Group

![](2022-04-27-06-28-42.png)

## Declouple between application tiers

![](2022-04-27-06-29-14.png)

## Security

- Encryption
    - In-flight encryption using HTTPS API
    - At-rest encryption using KMS Keys
    - Client-side encryption if the client wants to perform encryption/decryption itself
- Access Controls: IAM policies to regulate access to the SQS API
- SQS Access Policies (similar to S3 bucket policies)
    - Useful for cross-account access to SQS queues
    - Useful for allowing other services (SNS, S3...) to write to an SQS queue
