# API Gateway

- [[AWS Lambda]] + [[AWS API Gateway]] : no infrastructure to manage
- Handle [[API versioning]] (v1, v2)
- Handle different environments (dev, test, prod)
- Handle security ([[Authentication and Authorization]])
- Create [[API keys]], handle [[request throttling]]
- [[Swagger]] / [[Open API]] import to quickly define APIs
- Transform and validate requests and responses
- Generate [[SDK and API specifications]]
- [[Cache API]] responses

## API Gateway integrations

- Outside of [[VPC]]:
    - [[AWS Lambda]] (most popular / powerful)
    - Endpoints on [[AWS EC2]]
    - [[Programming/AWS/EC2/Elastic LoadBalancer/Load Balancing]]
    - Any AWS Service
    - External and publicly accessible HTTP endpoints
- Inside of VPC
    - [[AWS Lambda]] in your [[VPC]]
    - [[AWS EC2]] endpoints in your [[VPC]]

## Security

- IAM Permissions
    - Create an [[IAM Policy]] authorization and attach to User / Role
    - [[AWS API Gateway]] verifies [[02-iam-permissions-for-lambda-functions | IAM permissions]] passed by the calling application
    - Good to provide access within your own infrastructure
    - Leverages "[[Sig v4]]" capability where IAM credential are in headers
    - Great for users / roles already within your AWS account
- [[Lambda Authorized]] (formerly Custom Authorizers)
    - Uses [[AWS Lambda]] to validate the token in header being passed
    - Option to cache result of authentication
    - Helps to use [[Oauth]] / [[SAML]] / 3rd party type of authentication
    - Lambda must return an [[IAM Policy]] for the user
    - Pay per Lambda invocation
- [[Programming/AWS/AWS Serverless APIs/05-authenticating-users-with-cognito-and-api-gateway/AWS Cognito]] User Pools
    - Cognito fully manages [[user lifecycle]]
    - [[AWS API Gateway]] verifies identity automatically from [[Programming/AWS/AWS Serverless APIs/05-authenticating-users-with-cognito-and-api-gateway/AWS Cognito]]
    - No custom implementation required
    - Cognito only helps with [[authentication]], not [[authorization]]