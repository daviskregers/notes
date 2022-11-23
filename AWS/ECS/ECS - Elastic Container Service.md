---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ecs, review]
sr-due: 2022-11-24
sr-interval: 1
sr-ease: 130
---

# ECS - Elastic Container Service

- ECS is a container orchestration service
- ECS helps you run [[Docker container]]s on [[AWS EC2]] machines
- ECS is complicated and made of:
    - "[[ECS Core]]" : Running ECS on user-provisioned [[AWS EC2]] instances
    - [[Fargate]]: Running [[ECS task]]s on AWS-provisioned compute ([[serverless]])
    - [[AWS EKS]]: Running ECS on AWS-powered [[Kubernetes]] (running on [[AWS EC2]])
    - [[AWS ECR (Elastic Container Registry)]]: [[Docker]] [[Container Registry]] hosted by AWS
- [[ECS - Elastic Container Service]] & [[Docker]] are very popular for [[micro-service]]s
- [[IAM]] security and [[IAM Role]]s at the [[ECS task]] level

## ECS - Use cases

- Run [[micro-service]]s
    - Ability to run multiple [[docker container]]s on the same machine
    - Ease [[service discovery]] features to enhance communication
    - Direct integration with [[Application Load Balancer (v2)]]
    - [[Auto scaling]] capability
- Run [[batch processing]] / [[scheduled task]]s
    - Schedule [[AWS EC2]] containers to run [[EC2 On Demand Instances]] / [[EC2 Reserved Instances]] / [[EC2 Spot Instances]]
- [[Migrate]] applications to the [[cloud]]
    - Dockerize [[legacy application]]s running on premise
    - Move [[docker container]]s to run on [[ECS - Elastic Container Service]]

## AWS ECS - Concepts

- [[ECS cluster]]: set of EC2 instances
- [[ECS service]]: applications definitions running on ECS cluster
- [[ECS task]]s + definition: containers running to create the application
- [[ECS IAM role]]s: roles assigned to tasks to interact with AWS

![](2020-01-02-14-45-42.png)

[[AWS ECS - ALB Integration]]
[[AWS ECS Setup and Config File]]
[[AWS ECS - ECR Integration]]

