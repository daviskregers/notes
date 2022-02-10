# AWS Credentials Provider & Chain

- The CLI will look for credentials in this order:
    - Command line options --region, --output, --profile
    - Environment variables AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY, AWS_SESSION_TOKEN
    - CLI credentials file - ~/.aws/credentials 
    - CLI configuration file - ~/.aws/config
    - Container credentials - for ECS tasks
    - Instance profile credentials - for EC2 Instance Profiles

## AWS SDK Default Credentials Provider Chain

- The Java SDK (example) will look for credentials in this order:
    - Java system properties - aws.accessKeyId, aws.secretKey
    - Environment variables AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY
    - The default credential profiles file at ~/.aws/credentials
    - Amazon ECS container credentials - for ECS containers
    - Instance profile credentials - used on EC2 instances

## AWS Credentials Scenario

- An application deployed on an EC2 instance is using environment variables with credentials from an IAM user to call the Amazon S3 API.
- The IAM user has S3FullAccess permissions
- The application only uses one S3 bucket, so according to best practices:
    - An IAM Role & EC2 instance profile was created for the EC2 instance
    - The Role was assigned the minimum permissions to access that one S3 bucket
- The IAM Instance Profile was assigned to the EC2 instance, but it still had access to all S3 buckets. Why?
    - The credentials chain is still giving priorities to the environment variables
    - unset the environment variables

## AWS Credentials Best Practices

- Overall, NEVER STORE AWS CREDENTIALS IN YOUR CODE
- Best practice is for credentials to be inherited from the credentials chain
- If working within AWS, use IAM Roles
    - EC2 instance roles for EC2 instances
    - ECS Roles for ECS tasks
    - Lambda roles for lambda functions

- If working outside of AWS, use environment variables / named profiles