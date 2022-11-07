# Overview of the REST API service

We are going to create an API gateway and it will have multiple lambdas attached to it to serve CREATE/LIST/GET/UPDATE/DELETE endpoints.

The data will be persisted in a dynamo table.

## What we'll use:

- NodeJS runtime
- API Gateway
- DynamoDB table
- Function timeouts and memory
- IAM permissions
- CloudFormation Resources