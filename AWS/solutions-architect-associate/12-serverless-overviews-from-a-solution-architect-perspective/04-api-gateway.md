# API Gateway

- AWS Lamda + API Gateway : no infrastructure to manage
- Handle API versioning (v1, v2)
- Handle different environments (dev, test, prod)
- Handle security (Authentication and Authorization)
- Create API keys, handle request throttling
- Swagger / Open API import to quickly define APIs
- Transform and validate requests and responses
- Generate SDK and API specifications
- Cache API responses

## API Gateway integrations

- Outside of VPC:
    - AWS Lambda (most popular / powerful)
    - Endpoints on EC2
    - Load Balancers
    - Any AWS Service
    - External and publicly acessible HTTP endpoints
- Inside of VPC
    - AWS Lamda in your VPC
    - EC2 endpoints in your VPC

## Security

- IAM Permissions
    - Create an IAM policy authorization and attach to User / ROle
    - API Gateway verifies IAM permissions passed by the calling application
    - Good to provide access within your own infrastructure
    - Leverages "Sig v4" capability where IAM credential are in headers
    - Grat for users / roles already within your AWS account
- Lambda Authorized (formerly Custom Authorizers)
    - Uses AWS Lambda to validate the token in header being passed
    - Option to cache result of authentication
    - Helps to use Oauth / SAML / 3rd party type of authentication
    - Lamda must return an IAM policy for the user
    - Pay per Lamda invocation
- Cognito User Pools
    - Cognito fully manages user lifecycle
    - API gateway verifies identity automatically from AWS Cognito
    - No custom implementation required
    - Cognito only helps with authentication, not authorization