# ECS Task Placements

- When a task of thpe EC2 is launched, ECS must determine where to place it, with the constraints of CPU, memory and available port.
- Similarly, when a service scales in, ECS needs to determine which task to terminate.
- To assist with this, you can define a task placement strategy and task placement constraints.
- Note: this is only for ECS with EC2 not Fargate

![](2022-04-20-11-03-18.png)

## ECS Task Placement Process

- Task placement strategies are best effort
- When Amazon ECS places tasks, it uses the following process to select container instances:
    1. Identify the instances that satisfy the CPU, memory and port requirements in the task definition.
    2. Identify the instances that satisfy the task placement constraints.
    3. Identify the instances that satisfy the task placement strategies.
    4. Select the instance for task placement.

## ECS Task Placement Strategies

### Binpack

- Place tasks based on the least available amount of CPU or memory
- This minimizes the number of instances in use (cost savings)

```json
"placementStrategy": [
    {"field": "memory", "type": "binpack"}
]
```

### Random

- Place the task randomly

```json
"placementStrategy": [
    {"type": "random"}
]
```

### Spread

- Place the task evenly based on the specified value
- Example: instanceId, attribute:ecs.availability-zone

```json
"placementStrategy": [
    {"field": "attribute:ecs.availability-zone", "type": "spread"}
]
```

### Mix

- You can mix the strategies together:
    - spread by AZ and spread by instanceId
    - spread by AZ, binpack on memory

```json
"placementStrategy": [
    {"field": "attribute:ecs.availability-zone", "type": "spread"},
    {"field": "instanceId", "type": "spread"}
]
```

```json
"placementStrategy": [
    {"field": "attribute:ecs.availability-zone", "type": "spread"},
    {"field": "memory", "type": "binpack"}
]
```

## Task Placement Constraints

- distinctInstance: place each task on a different container instance

```json
"placementConstraints": [
    {"type": "distinctInstance"}
]
```

- memberOf: place task on instances that satisfy an expression
    - uses cluster Query Language (advanced)

```json
"placementConstraints": [
    {
        "expression": "attribute.ecs.instance-type =~ t2.*",
        "type": "memberOf"
    }
]
```