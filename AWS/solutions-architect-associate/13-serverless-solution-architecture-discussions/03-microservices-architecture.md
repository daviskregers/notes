# Micro Services architecture

- We want to switch to a micro service architecture
- Many services interact with each other directly using a REST API
- Each architecture for each micro service may vary in form and shape
- We want a micro-service architecture so we can have a leaner development lifecycle for each service.

![](2020-01-01-12-22-44.png)

## Discussions on Micro Services

- You are free to design each micro-service the way you want
- Synchronous patterns: API Gateway, Load Balancers
- Asynchronous patterns: SQS, Kinesis, SNS, Lambda triggers (S3)
- Challenges with micro-services:
    - Repeated overhead for creating each new microservice
    - Issues with optimizing server density/utilizaion
    - Complexity of running multiple versions of multiple microservices simultaneously
    - proliferation of client-side code requirements to integrate with many seperate services.
- Some of the challenges are solved by Serverless patterns:
    - API Gateway, Lamda scale automatically and you pay per usage
    - You can easily clone API, reproduce environments
    - Generate client SDK through Swagger integration for the API Gateway

