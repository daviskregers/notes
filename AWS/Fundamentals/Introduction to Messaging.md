---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/fundamentals]
---

# Introduction to Messaging

- When we start to deploying multiple applications, they will inevitably need to communicate with one another
- There are two patterns of application communication
    - [[Synchronous communications]] (application to application)
    - [[Asynchronous]] / [[Event based]] (application to queue to application)
- Synchronous between applications can be problematic if there are sudden spikes of traffic
- What if you need to suddenly encode 1000 videos but usually it's 10?
    - in that case it's better to decouple your applications
        - using [[AWS SQS | SQS]]: queue model
        - using [[AWS SNS | SNS]]: pub/sub model
        - using [[Kinesis | Kinesis]]: real-time streaming model
    - These services can scale independently from our application