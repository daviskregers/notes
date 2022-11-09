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

## AWS SQS - FIFO Queue

- Newer offering (First In - First Out - [[FIFO]]) - not available in all regions
- Name of the queue must end in .fifo
- Lower [[throughput]] (up to 3,000 per second with batching, 300/s without)
- Messages are processed in order by the consumer
- Messages are sent exactly once
- No per message delay (only per queue delay)
- Ability to do content based [[de-duplication]]
- 5 minute interval de-duplication using "Duplication ID"
- Message groups
    - Possibility to group messages for [[FIFO]] ordering using "Message GroupID"
    - Only one worker can be assigned per message group so that messages are processed in order
    - Message group is just an extra tag on the message