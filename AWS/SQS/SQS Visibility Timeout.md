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

## SQS - Visibility Timeout

- When a consumer polls a message from a queue, the message is "invisible"'to other consumers for a defined period. The Visibility Timeout.
- You can set between 0 seconds and 12 hours (default to 30 seconds).
    - If you set too high (15 minutes) and consumer fails to process the message, you must wait a long time before processing the message again.
    - If you set too low (30 seconds) and consumer needs time to process the message (2 minutes), another consumer will receive the message will be processed more than once.
- ChangeMessageVisibility API to change the visibility while processing a message.
- DeleteMessage API to tell SQS the message was successfully procesed.