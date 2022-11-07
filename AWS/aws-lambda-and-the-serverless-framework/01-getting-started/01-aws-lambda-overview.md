# AWS Lambda Overview

## What is AWS

- AWS is a Cloud Provider
- They provide you with servers and services that you can use on demand and scale easily.
- AWS has revolutionized IT over time
- AWS powers some of the biggest websites in the world (for example Netflix)
- Recently (Nov 2014) they introduced AWS Lambda

## Why AWS Lambda

### EC2
- Virtual Servers in the Cloud
- Limited by RAM and CPU
- Continuously running
- Scaling means intervention to add / remove servers

### Lambda
- Virtual functions - no servers to manage.
- Limited by time - short executions
- Run on-demand
- Scaling is automated

## Benefits of AWS Lambda

- Easy pricing
    - Pay per request and compute time
    - Free tier of 1,000,000 AWS Lambda requests and 400,000 GBs of compute time
- Integrated with the whole AWS Stack
- Integrated with many programming languages
- Easy monitoring through AWS CloudWatch
- Easy to get more resources per functions (up to 1.5GB of ram)
- Increasing RAM will also improve CPU and network

## AWS Lambda Languages

- aws-nodejs
- aws-python
- aws-python3
- aws-groovy-gradle
- aws-java-gradle
- aws-java-maven
- aws-scala-sbt
- aws-csharp

## AWS Lambda Integrations - main ones

- API Gateway
- Kinesis
- DynamoDB
- AWS S3
- AWS IoT
- CloudWatch Events
- CloudWatch Logs
- AWS SNS
- AWS Congnito

## Example: thumbnail creation

- A new image gets uploaded to S3
- Triggers AWS Lambda Function that creates a thumbnail
- New thumbnail gets uploaded to S3
- Metadata uploaded into DynamoDB