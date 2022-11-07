# Beanstalk overview

## Developer problems on AWS

- Managing infrastructure
- Deploying Code
- Configuring all the databases, load balancers etc
- Scaling concerns
- Most web apps have the same architecture (ALB+ASG)
- All the developers want their code to run
- Possibly, consistently accross different applications and environments

## AWS ElasticBeanStalk Overview

- ElasticBeanstalk is a developer centric view of deploying an application on AWS
- It uses all the components we've seen before: EC2, ASG, ELB, RDS etc.
- But it's all in one view that's easy to make sense of.
- We still have full control over configuration
- BeanStalk is free but you pay for the underlying instances.

- It is a Managed Service
    - Instance Configuration / OS is handled by beanstalk
    - Deployment strategy is configurable but performed by ElasticBeanStalk
- Just the application code is the responsibility of the developer

- Three architecture models:
    - Single Instance deployment: good for dev
    - LB + ASB: great for production or pre-production web-applications
    - ASG only: great for non-web apps in production (workers, etc)

- ElasticBeanStalk has three components:
    - Application
    - Application version: each deployment gets assigned a version
    - Environment name (dev, test, prod): free naming
- You deploy application versions to environments and can promote application versions to the next environment
- Rollback feature to previous application versions
- Full control over lifecycle of environments

- Support for many platforms:
    - Go
    - Java SE
    - Java with Tomcat
    - .NET on WIndows Server with IIS
    - Node.js
    - PHP
    - Python
    - Ruby
    - Packer Builder
    - Single Container Docker
    - Multicontainer DOcker
    - Preconfigured Docker
    - If not supported, you can write your custom platform.

