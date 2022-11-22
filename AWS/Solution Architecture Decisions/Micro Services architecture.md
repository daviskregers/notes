---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/architecture, review]
sr-due: 2022-11-25
sr-interval: 3
sr-ease: 230
---

# Micro Services architecture

- We want to switch to a [[micro-service architecture]]
- Many services interact with each other directly using a [[REST API]]
- Each architecture for each micro service may vary in form and shape
- We want a [[micro-service architecture]] so we can have a leaner [[development lifecycle]] for each service.

![](2020-01-01-12-22-44.png)

## Discussions on Micro Services

- You are free to design each [[micro-service]] the way you want
- Synchronous patterns: [[AWS API Gateway]], [[Load Balancer]]s
- Asynchronous patterns: [[AWS SQS]], [[Kinesis]], [[AWS SNS]], [[Lambda Triggers]] (S3)
- Challenges with micro-services:
    - Repeated [[overhead for creating each new microservice]]
    - Issues with [[optimizing server density, utilizaion]]
    - Complexity of [[running multiple versions of multiple micro-services simultaneously]]
    - [[proliferation of client-side code requirements to integrate with many seperate services]].
- Some of the challenges are solved by Serverless patterns:
    - [[AWS API Gateway]], [[AWS Lambda]] scale automatically and you pay per usage
    - You can easily clone [[API]], [[reproduce environments]]
    - [[Generate client SDK through Swagger integration for the API Gateway]]