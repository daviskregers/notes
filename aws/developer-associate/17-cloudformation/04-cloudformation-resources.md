# CloudFormation Resources

## What are resources?

- Resources are the core of your CloudFormation template (mandatory)
- They represent the different AWS Components that will be created and configured
- Resources are declared and can reference each other

- AWS figures out creation, updates and deletes of resources for us
- There are over 224 types of resources
- Resource types identifiers are of the form:
    - `AWS::aws-product-name::data-type-name`

## How do I find resources documentation?

- All the resources can be found in https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-template-resource-type-ref.html
- An EC2 instance example is here: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-ec2-instance.html

## FAQ for resources

- Can I create dynamic amount of resources?
    - No, you can't. Everything in CloudFormation template has to be declared. You can't perform code generation there.
- Is every AWS Service supported?
    - Almost. Only a few select few niches are not there yet.
    - You can work around that usin AWS Lambda Custom Resources