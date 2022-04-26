# CloudFormation Outputs

- The outputs section declares optional outputs values that we can import into other stacks (if you export them first)
- You can also view the outputs in the AWS Console or in using the AWS CLI
- They're very useful for example if you define a network CloudFormation, and output the variables such as VPC ID and your Subnet ID
- It's the best way to perform some collaboration cross stack, as you let exper handle their own part of the stack
- You can't delete a CloudFormation Stack if its output are being referenced by another CloudFormation stack

## Outputs Example

- Creating an SSH Security Group as part of one template
- We create an output that references that security group

```yml
Outputs:
    StackSSHSecurityGroup:
        Description: The SSH Security Group for our company
        Value: !Ref MyCompanyWideSSHSecurityGroup
        Export:
            Name: SSHSecurityGroup
```

## Cross Stack Reference

- We then create a second template that leverages that security group
- For this, we use the `Fn::ImportValue` function
- You can't delete the underlying stack until all the references are deleted too.

```yml
Resources:
    MySecureInstance:
        Type: AWS::EC2::Instance
    Properties:
        AvailabilityZone: us-east-1a
        ImageId: ami-a4c7edb2
        InstanceType: t2.micro
        SecurityGroups:
            - !ImportValue SSHSecurityGroup
```