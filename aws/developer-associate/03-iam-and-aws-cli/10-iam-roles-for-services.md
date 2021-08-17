# IAM Roles for Services

Some services in AWS need to perform actions on your behalf. For this, just like users, they will need permissions.

To do this, we will assign permissions to AWS services with IAM Roles.

For example, we will create an EC2 instance. This EC2 instance may want to perform some actions on AWS. In order to do this, we need to give this EC2 instance permissions to do these actions.

Some of the most common roles we are going to use:
- EC2 Instance Roles
- Lambda Function Roles
- Roles for CloudFormation

