# VPC for lambda functions

- VPC are Virtual Private Clouds
    - Many companies use VPC to privately deploy their applications
    - By default Lambda functions are not launched in a VPC
- But you can launch lambda in your VPC, so that your lambda functions can securely access your resources.

- You can also assign security groups to your lambda functions as well for enhanced network security.

---

- You can choose to deploy your lambda function in any subnets you like.
- This will allow your lambda function to inherit a private IP from that subnet.

```yaml
service: service-04-python-example-vpc
frameworkVersion: '2'
provider:
  name: aws
  runtime: python2.7
  lambdaHashingVersion: 20201221
  profile: serverless-admin
  vpc:
    securityGroupIds:
      - sg-XXXX
    subnetIds:
      - subnet-XXX
      - subnet-XXX
functions:
  hello:
    handler: handler.hello
```