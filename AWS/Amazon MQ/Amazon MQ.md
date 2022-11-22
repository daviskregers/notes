---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/amazon-mq, review]
sr-due: 2022-12-15
sr-interval: 23
sr-ease: 250
---

# Amazon MQ

- [[AWS SQS]], [[AWS SNS]] are "cloud-native" services, and they're using proprietary protocols from AWS.
- Traditional applications running from on-premise may use open protocols such as [[MQTT]], [[AMQP]], [[STOMP]], [[Openwire]], [[WSS]]
- When migrating to [[cloud]], instead of re-engineering the application to use [[AWS SQS]] and [[AWS SNS]], we can use Amazon MQ
- Amazon MQ = managed [[Apache ActiveMQ]]
- Amazon MQ doesn't scale as much as [[AWS SQS]] / [[AWS SNS]]
- Amazon MQ runs on a dedicated machine, can run in [[High Availability failover]]
- Amazon MQ has both queue feature (~[[AWS SQS]]) and topic features (~[[AWS SNS]])