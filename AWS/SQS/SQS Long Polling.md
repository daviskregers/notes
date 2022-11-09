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

## AWS SQS - Long Polling

- When a consumer requests message from the queue, it can optionally wait for messages to arrive if there are none in the queue.
- This is called [[long polling]]
- LongPolling decreases the number of [[API]] calls made to [[AWS SQS]] while increasing the efficiency and latency of your application.
- The wait time can be between 1 to 20 sec (20 sec preferable)
- Long Polling is preferable to short polling
- Long polling can be enabled at the queue level or at the API level using WaitTimeSeconds