# CloudFormation Intrinsic Functions

Some of the intrinsic functions:
- Ref
- Fn::GetAtt
- Fn::FindInMap
- Fn::ImportValue
- Fn::Join
- Fn::Sub
- Condition Functions (Fn::If, Fn::Not, Fn::Equals, etc)

## Fn::Ref

- The Fn::Ref function can be leveraged to reference
    - parameters -> returns the value of the parameter
    - resources -> returns the physical ID of the underlying resource
- The shorthand for this in YAML is `!Ref`

```yml
DbSubnet1:
    Type: AWS::EC2::Subnet
    Properties:
        VpcId: !Ref MyVPC
```

## Fn::GetAtt

- Attributes are attached to any resource you create
- To know the attributes of your resources, the best place to look at is the documentation

```yml
Resources:
    EC2Instance:
        Type: AWS::EC2::Instance
        Properties:
            ImageId: ami-1234567
            InstanceType: t2.micro
    NewVolume:
        Type: AWS::EC2::Volume
        Condition: CreateProdResources
        Properties:
            Size: 100
            AvailabilityZone:
                !GetAtt EC2Instance.AvailabilityZone
```

## Fn::FindInMap

- We use Fn::FindInMap to return a named value from a specific key

```yml
RegionMap:
    us-east-1:
        "32": "ami-6411e20d"
        "64": "ami-7a11e213"
    us-west-1:
        "32": "ami-c9c7978c"
        "64": "ami-cfc7978a"
    eu-west-1:
        "32": "ami-37c2f643"
        "64": "ami-31c2f645"
Resources:
    myEc2Instance:
        Type: AWS::EC2::Instance
        Properties:
            ImageId: !FindInMap [RegionMap, !Ref AWS::Region, 32]
        InstanceType: m1.small        
```

You can reference the map using

```
!FindInMap [ MapName, TopLevelKey, SecondLevelKey ]
```

## Fn::ImportValue

- Import values that are exported in other templates

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

## Fn::join

- Join values with a delimiter

```
!Join [ delimiter, [ comma-delimited list of values ] ]
```

This creates "a:b:c"

```
!Join [ ":", [ a, b, c ] ]
```

## Fn::Sub

- Sn::Sub or !Sub as a shorthand is used to substitute variables from a text. It's a very handy function that will allow you to fully customize your templates.
- For example you can combine Fn::Sub with references or AWS Pseudo variables.
- String must contain ${variableName} and will substitute them

```
!Sub
    - String
    - {Var1Name: Var1Value, Var2Name: Var2Value }
```

```
!Sub String
```

### Condition Functions

```yml
Conditions:
    CreateProdResources: !Equal [ !Ref EnvType, prod ]
```

- The logical ID is for you yo choose. It's how you name condition
- The intrinsic function (logical) can be any of the following:
    - Fn::And
    - Fn::Equals
    - Fn::If
    - Fn::Not
    - Fn::Or
