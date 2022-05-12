# Lambda Best Practices

- Perform heavy-duty work outside of your function handler
    - Connect to databases outside of your function handler
    - Initialize the AWS SDK outside of your function handler
    - Pull in dependencies or datasets outside your function handler
- Use environment variables for:
    - Database Connection Strings, S3 bucket, etc... don't put these values in your code
    - Passwords, sensitive values... they can be encrypted using KMS
- Minimize your deployment package size to it's runtime necessities
    - Break down the function if need be
    - Remember the AWS Lambda limits
    - Use layers where necessary
- Avoid using recursive code, never have a lambda call itself. Can be a very expensive disaster.
