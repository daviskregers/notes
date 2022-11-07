# Amazon SNS

- What if you want to send one message to many receivers?

![](2022-04-27-07-11-15.png)

- The "event producer" only sends message to SNS topic
- As many "event receivers" (subscriptions) as we want to listen to the SNS topic notifications
- Each subscriber to the topic will get all the messages (note: new feature to filter messages)
- Up to 12,500,000 subscriptions per topic
- 100,000 topics limit

![](2022-04-27-07-12-52.png)

- Many AWS services can send data directly to SNS for notifications

![](2022-04-27-07-13-23.png)

## How to publish

- Topic Publish (using the SDK)
    - Create a topic
    - Create a subscription (or many)
    - Publish to the topic
- Direct publish (for mobile apps SDK)
    - Create a platform application
    - Create a platform endpoint
    - Publish to the platform endpoint
    - Works with Google GCM, Apple APNS, Amazon ADM

## Security

- Encryption:
    - In-flight encryption using HTTPS API
    - At-rest encryption using KMS
    - Client-side encryption if the client wants to perform encryption/decryption itself
- Access Controls: IAM policies to regulate access to the SNS API
- SNS Access Policies (similar to S3 bucket policies)
    - useful for cross-account access to SNS topics
    - Useful for allowing other services (s3...) to write to an SNS topic

 