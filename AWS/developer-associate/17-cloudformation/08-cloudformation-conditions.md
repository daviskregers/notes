# CloudFormation Conditions

- Conditions are used to control the creation of resources or outputs based on a condition.
- Conditions can be whatever you want them to be, but common ones are:
    - Environment (dev / test / prod)
    - AWS Region
    - Any parameter value
- Each condition can reference another condition, parameter value or mapping

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

- These can be applied to resources / outputs etc

```yml
Resources:
    MountPoint:
        Type: AWS::EC2::VolumeAttachment
        Condition: CreateProdResources
```