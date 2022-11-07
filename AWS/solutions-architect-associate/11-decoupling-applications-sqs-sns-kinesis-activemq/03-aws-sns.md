# AWS SNS

- The "event producer" only sends message to one SNS topic
- As many "event receivers" (subscriptions) as we want to listen to the SNS topic notifications
- Each subscriber to the topic will get all the messages (note: new feature to filter messages)
- Up to 10,000,000 subscriptions per topic
- 100,000 topics limit
- Subscribers can be:
    - SQS
    - HTTP / HTTPS (with delivery retries - how many times)
    - Lambda
    - Emails
    - SMS messages
    - Mobile notifications

## SNS integrates with a lot of Amazon Products

- Some services can send data directly to SNS for notifications
- CloudWatch (for alarms)
- Auto Scaling Groups notifications
- Amazon S3 (on bucket events)
- CloudFormation (upon state changes => failed to build etc)
- Etc

## SNS - How to publish

- Topic Publish (within you AWS server - using the SDK)
    - Create a topic
    - Create a subscription (or many)
    - Publish to the topic

- Direct Publish (for mobile apps SDK)
    - Create a platform application
    - Create a platform endpoint
    - Publish to the platform endpoint
    - Works with Google GCM, Apple APNS, Amazon ADM...

## SNS + SQS: Fan Out

- Publish once in SNS, receive in many SQS
- Fully decoupled
- No data loss
- Ability to add receivers of data later
- SQS allows for delayed processing
- SQS allows for retries of work
- May have many workers on one queue and one worker on the othere queue

![](2019-12-31-10-29-31.png)

## Hands on

You can type `SNS` or `Simple Notification Service` in AWS Console.

![](2019-12-31-10-31-17.png)

Then create `MyFirstTopic`.

![](2019-12-31-10-32-30.png)

![](2019-12-31-10-32-53.png)

Now create a subscription.

![](2019-12-31-10-34-05.png)

Confirm subscription

![](2019-12-31-10-34-48.png)

![](2019-12-31-10-35-17.png)

Now publish a message.

![](2019-12-31-10-36-10.png)

![](2019-12-31-10-36-38.png)