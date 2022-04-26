# CloudFormation Overview

## Infrastructure as Code

- Currently, we have been doing a lot of manual work
- All this manual work will be very tough to reproduce:
    - In another region
    - In another AWS account
    - Within the same region if everything was deleted
- Wouldn't it be great, if all our infrastructure was... code?
- That code would be deployed and create / update / delete our infrastructure.

## CloudFormation

- CloudFormation is a declarative way of outlining our AWS Infrastructure, for any resources (most of them are supported).
- For example, within a CloudFormation template, you say:
    - I want a security group
    - I want two EC2 machines using this security group
    - I want two Elastic IPs for these EC2 machines
    - I want an S3 bucket
    - I want a load balancer (ELB) if front of these machines
- Then CloudFormation creates those for you, in the right order, with the exact configuration you specify.

## Benefits of AWS CloudFormation

- Infrastructure as code
    - No resources are manually creasted, which is excellent for control
    - The code can be version controlled for example using git
    - Changes to the infrastructure are reviewed through code
- Cost
    - Each resource within the stack is tagged with an identifier so you can easily see how much a stack costs you
    - You can estimate the costs of your resources using CloudFormation template
    - Savings strategy: In Dev, you could automate deletion of templates at 5pm and recreate at 8am safely.
- Productivity
    - Ability to destroy and re-create an infrastructure on the cloud on the fly
    - Automated generation of Diagram for your templates
    - Declarative programming (no need to figure out ordering and orchestration)
- Separation of concern: create many stacks for many pps, and many layers. Ex: VPC stacks, network stacks, App stacks.
- Don't re-invent the wheel
    - Leverage existing templates on the web!
    - Leverage the documentation!

## How CloudFormation Works

- Templates have to be uploaded in S3 and then referenced in CloudFormation
- To update a template, we can't edit previous ones. We have to re-upload a new version of the template to AWS
- Stacks are identified by a name
- Deleting a stack deletes every single artifact that was created by CloudFormation

## Deploying CloudFormation templates

- Manual way:
    - Editing templates in the cloudformation designer
    - using the console to input parameters
- Automated way:
    - Editing templates in a YAML file
    - Using the AWS CLI to  deploy the templates
    - Recommended way when you fully want to automate your flow

## ClouFormation Building Blocks

### Template components
- Resources: your AWS resources declared in the template (mandatory)
- Parameters: the dynamic inputs for your template
- Mappings: the static variables for your template
- Outputs: references to what has been created
- Conditionals: list of conditions to perform resource creation
- Metadata

### Template helpers:
- References
- Functions