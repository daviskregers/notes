# CodeBuild Overview

- Source - CodeCommit, S3, BitBucket, GitHub
- Build Instructions: code file buildspec.yml or insert manually in Console
- Output logs can be stored in Amazon S3 & CloudWatch Logs
- Use CloudWatch Metrics to monitor build statistics
- Use CloudWatch Events to detect failed builds and trigger notifications
- Use CloudWatch Amarms to notify if you need "thresholds" for failures

- Build Projects can be defined within CodePipeline or CodeBuild

## Supported Environment

- Java
- Ruby
- Python
- Go
- Node.js
- Android
- .NET Core
- PHP
- Docker - extend any environment you like

## How It works

![](2022-04-21-08-39-55.png)

## buildspec.yml

- buildspec.yml file must be at the root of your code
- env - define environment variables
    - variables - plain text variables
    - parameter-store - variables stored in SSM Parameter Store
    - secrets-manager - variables stored in AWS Secret Manager
- phases - specify commands to run
    - install - install dependencies you may need for your build
    - pre_build - final commands to execute before build
    - build - actual build commands
    - post_build - finishing touches (e.g. zip output)
- artifacts - what to upload to S3 (encrypted with KMS)
- cache - files to cache (usually dependencies) to S3 for future build speedup

```yml
version: 0.2
env:
    variables:
        JAVA_HOME: "/usr/lib/jvm/java-8-openjdk-amd64"
    parameter-store:
        LOGIN_PASSWORD: /CodeBuild/dockerLoginPassword
phases:
    install:
        commands:
            - echo "Entered the install phase..."
            - apt-get update -y
            - apt-get install -y maven
    pre_build:
        commands:
            - echo "Entered the pre_build phase..."
            - docker login -u User -p $LOGIN_PASSWORD
    build:
        commands:
            - echo "Entered the build phase..."
            - echo Build started on `date`"
            - mvn install
    post_build:
        commands:
            - echo "entered the post_build phase..."
            - echo "Build completed on `date`"
artifacts:
    files:
        - target/messageUtil-1.0.jar
cache:
    paths:
        - "/root/.m2/**/*"
```

## Local Build

- In case of need of deep troubleshooting beyon logs..
- You can run CodeBuild locally on your desktop (after installing Docker)
- For this, leverage CodeBuild Agent
    - https://docs.aws.amazon.com/codebuild/latest/userguide/use-codebuild-agent.html

## Inside VPC

- By default, you CodeBuild containers are launched outside your VPC
    - it cannot access resources in a VPC
- You can specify a VPC configuration:
    - VPC ID
    - Subnet IDs
    - Security Group IDs
- Then your build can access resources in your VPC (e.g. RDS, ElastiCache, EC2, ALB, ...)
- Use cases: integration tests, data query, internal load balancers,...