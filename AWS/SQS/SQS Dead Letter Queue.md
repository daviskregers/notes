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

## AWS SQS - Dead Letter Queue

- If a consumer fails to process a message within the visibility timeout the message goes back to the queue.
- We can set a threshold of how many times a message can go back to the queue - it's called a "[[redrive policy]]"
- After the threshold is exceeded, the message goes into a dead letter queue (DLQ)
- We have to create a DLQ first and then designate it dead letter queue
- Make sure to process the messages in the DLQ before they expire.