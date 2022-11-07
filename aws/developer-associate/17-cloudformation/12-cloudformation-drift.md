# CloudFormation Drift

- CloudFormation allows you to create infrastructure
- But it doesn't protect you against manual configuration changes
- How do we know if our resources have drifted?

- We can use CloudFormation drift
- Not all resources are supported yet:
    - https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-stack-drift-resource-list.html

In order to detect the drift, we can choose it under stack actions.

![](2022-04-21-11-50-31.png)

![](2022-04-21-11-50-59.png)