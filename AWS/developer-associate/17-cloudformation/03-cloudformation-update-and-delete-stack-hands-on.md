# CloudFormation Update and Delete Stack Hands On

We can select our stack and click on `update`. Then you can choose how you want to update it. We are going to upload a new file.

```yml
---
Parameters:
    SecurityGroupDescription:
        Description: Security Group Description
        Type: String
Resources:
    MyInstance:
        Type: AWS::EC2::Instance
        Properties:
            AvailabilityZone: us-east-1a
            ImageId: ami-a4c7edb2
            InstanceType: t2.micro
            SecurityGroups:
                - !Ref SSHSecurityGroup
                - !Ref ServerSecurityGroup
    MyEIP:
        Type: AWS::EC2::EIP
        Properties:
            InstanceId: !Ref MyInstance
    SSHSecurityGroup:
        Type: AWS::EC2::SecurityGroup
        Properties:
            GroupDescription: Enable SSH access via port 22
            SecurityGroupIngress:
                - CidrIp: 0.0.0.0/0
                  FromPort: 22
                  IpProtocol: tcp
                  ToPort: 22
    ServerSecurityGroup:
        Type: AWS::EC2::SecurityGroup
        Properties:
            GroupDescription: !Ref SecurityGroupDescription
            SecurityGroupIngress:
                - CidrIp: 0.0.0.0/0
                  FromPort: 80
                  IpProtocol: tcp
                  ToPort: 80
                - CidrIp: 192.168.1.1.1/32
                  FromPort: 22
                  IpProtocol: tcp
                  ToPort: 22
```

![](2022-04-21-10-47-44.png)

Now we'll get prompted to input a parameter.

![](2022-04-21-10-48-15.png)

In the review we'll see that we'll add a bunch of stuff, but will modify the already existing instance.

![](2022-04-21-10-48-56.png)

---

We can also select the cloudformation stack and click on delete. It will delete all the resources created.