# CloudFormation Mappings

- Mappings are fixed variables within your CloudFormation Template.
- They're very handy to differentiate between different environments (dev vs prod), regions (AWS regions), AMI types etc
- All the Values are hardcoded within the template:

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

## When would you use mappings vs parameters?

- Mappings are great when you know in advance all the values that can be taken and that they can be deducted from variables such as:
    - Region
    - Availability Zone
    - AWS Account
    - Environment (dev vs prod)
    - etc
- They allow safer control over the template
- Use parameters when the values are really user specific

