# CloudFormation ChangeSets, Nested Stacks, StackSet

## ChangeSets

- When you update a stack, you need to know what changes before it happens for greater condidence
- ChangeSets won't say if the update will be successful

![](2022-04-21-11-42-36.png)

## Nested Stacks

- Nested stacks are stacks as part of other stacks
- They allow you to isolate repeated patterns / common components in separate stacks and call them from other stacks
- Example:
    - Load Balancer configuration that is re-used
    - Security Group that is re-used
- Nested stacks are considered best practice
- To update a nested stack, always update the parent (root stack)

## Cross vs Nested Stacks

- Cross Stacks
    - Helpful when stacks have different lifecycles
    - Use Outputs Export and Fn::ImportValue
    - When you need to pass export values to many stacks (VPC Id, etc)

![](2022-04-21-11-46-24.png)

- Nested Stacks
    - Helpful when components must be re-used
    - Ex: re-use how to properly configure an Application Load Balancer
    - The nested stack only is important to the higher level stack (it's not shared)

![](2022-04-21-11-46-32.png)

## StackSets

- Create, update or delete stacks across multiple accounts and regions with a single operation
- Administrator account to create StackSets
- Trusted accounts to create, update, delete stack instances from StackSets
- When you update a stack set, all associated stack instances are updated throughout all accounts and regions.

![](2022-04-21-11-47-44.png)