# AWS SDK Overview

- What if you want to perform actions on AWS directly from your applications code? (without using the CLI)
- You can use an SDK (software development kit)
- Official SDKs are
    - Java
    - .NET
    - Node.js
    - PHP
    - Python (named boto3 / botocore)
    - Go
    - Ruby
    - C++

---

- We have to use the AWS SDK when using AWS Services like DynamoDB
- The AWS CLI uses the python SDK (boto3)
- The exam expects you to know when youu should use an SDK
- Good to know: if you don't specify or configure a default region, then us-east-1 will be chosen by default