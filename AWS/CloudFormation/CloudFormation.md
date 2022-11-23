---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/cloudformation, review]
sr-due: 2022-11-24
sr-interval: 1
sr-ease: 130
---

# CloudFormation

## What is CloudFormation

- CloudFormation is a [[declarative]] way of outlining your AWS [[Infrastructure]], for any  resources (most of them are supported).
- For example, within a CloudFormation template, you say:
    - I want a [[security group]]
    - I want two [[AWS EC2]] machines using this [[security group]]
    - I want two [[Elastic IP]]s for these [[AWS EC2]] machines
    - I want an [[AWS S3 Bucket]]
    - I want a [[Elastic Load Balancer]] in front of these machines
- Then CloudFormation creates those for you, in the right order, with the exact configuration you specify.

## Benefits of AWS CloudFormation

- [[Infrastructure as code]]
    - No resources are manually created, which is excellent for control
    - The code can be [[version controlled]] for example, using [[git]]
    - Changes to the [[infrastructure]] are [[reviewed]] through code
- Cost
    - Each resources within the stack are tagged with an identifier so you can easily see how much stack costs you
    - You can estimate the costs of your resources using the [[CloudFormation template]]
    - [[Savings strategy]]: in dev, you could make automation that deletes templates at 5pm and recreates them at 8am safely.
- Productivity
    - Ability to destroy and re-create an infrastructure on the cloud on the fly
    - Automated generation of [[Diagram]] for your templates
    - [[Declarative programming]] (no need to figure out ordering and orchestration)
- Separation of concern - create many stacks for many apps, and many layers
    - [[VPC stack]]s
    - [[Network stack]]s
    - [[App stack]]s
- Don't re-invent the wheel
    - Leverage existing templates on the web!
    - Leverage [[documentation]]

## How CloudFormation works

- Templates have to be uploaded in [[AWS S3]] and then referenced in [[CloudFormation]]
- To update a template, we can't edit previous ones. We have to re-upload a new version of the template to AWS
- Stacks are identified by a name
- Deleting a stack deletes every single [[artifact]] was created by [[CloudFormation]]

## Deploying CloudFormation templates

- Manual way:
    - Editing templates in the [[CloudFormation Designer]]
    - Using the console to [[input parameter]]s, etc
- Automated way
    - Editing templates in a [[YAML]] file
    - Using the [[AWS CLI]] to [[deploy]] the templates

## Templates components
    
- Resources components
    - Resources: your AWS resources declared in the template (mandatory)
    - Parameters: the [[dynamic input]]s for your template
    - Mappings: the [[static variable]]s for your template
    - Outputs: [[Reference]]s to what has been created
    - Conditionals: List of [[condition]]s to perform resource creation
    - [[Metadata]]
- Templates helpers
    - [[Reference]]s
    - [[Function]]s

## Hands On

When creating a new stack, you can choose between 3 options:
- Upload your template
- Use a sample template
- Design your template in a [[GUI]] way

![](2020-01-02-14-35-11.png)

![](2020-01-02-14-37-08.png)
