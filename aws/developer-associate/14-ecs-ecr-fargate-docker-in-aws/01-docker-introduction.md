# Dock Introduction

## What is docker

- Docker is a software development platform to deploy apps
- Apps are packaged in containers that can be run on any OS
- Apps run the same, regardless of where they're run
    - Any machine
    - No compatibility issues
    - Predictable behavior
    - Less work
    - Easier to maintain and deploy
    - Works with any language, any OS, any technology
- Use cases: microservices architecture, lift-and-shift apps from on-premises to AWS cloud, ...

## Where are Docker images stored?

- Docker images are stored in repositories
    - Docker Hub (https://hub.docker.com)
        - public repository
        - find base images for many technologies or OS (e.g. ubuntu, mysql)
    - Amazon ECR (Amazon Elastic Container Registry)
        - private repository
        - public repository (Amazon ECR Public Gallery https://gallery.ecr.aws)

## Docker vs Virtual Machines

- Docker is "sort of" a virtualization technology, but not exactly
- Resources are shared with the host to many containers on one server

![](2022-04-20-08-39-29.png)

## Docker Containers Management on AWS

- Amazon Elastic Container Service (Amazon ECS)
    - Amazon's own container platform
- Amazon Elastic Kubernetes Service (Amazon EKS)
    - Amazon's managed Kubernetes (Open Source)
- AWS Fargate
    - Amazon's own serverless container platform
    - Works with ECS and with EKS
- Amazon ECR:
    - Store container images