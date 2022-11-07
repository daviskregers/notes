# Amazon ECS - Task Definitions

- Task definitions are metadata in JSON format to tell ECS how to run a Docker container
- It contains crucial information, such as:
    - Image name
    - Port binding for Container and Host
    - Memory and CPU required
    - Environment Variables
    - Networking information
    - IAM Role
- Can define up to 10 containers in a task definition

## Load Balancing (EC2 Launch Type)

- We get a Dynamic Host Port Mapping if you define only the container port in the task definition
- The ALB finds the right port on your EC2 instances.
- You must allow on the EC2 instance's Security group any port from the ALB's Security Group

![](2022-04-20-10-47-53.png)

## Load Balancing (Fargate)

- Each task has a unique private IP
- Only define the container port (host port is not applicable)
- Example
    - ECS ENI Security Group
        - Allow port 0 from the ALB
    - ALB Security Group
        - Allow port 80/443 from web

![](2022-04-20-10-49-37.png)

## One IAM Role per Task Definition

IAM roles are assigned per task definition. Each ECS task will asume the provided role.

![](2022-04-20-10-50-40.png)

## Environment Variables

- Environment Variable
    - Hardcoded - e.g. URLs
    - SSM Parameter Store - sensitive variables (e.g. API keys, shared configs)
    - Secrets Manager - sensitive variables (e.g. DB passwords)
- Environment Files (bulk) - Amazon S3

![](2022-04-20-10-53-02.png)

## Data Volumes (Bind Mounts)

- Share data between multiple containers in the same task definition
- Works for both EC2 and Fargate tasks
- EC2 tasks - using EC2 instance storage
    - data are tied to the lifecycle of the EC2 instance
- Fargate tasks - using ephemeral storage
    - Data are tied to the contain(s) using them
    - 20 GiB - 200 GiB (default 20 GiB)

- Use cases:
    - Share ephemeral data between multiple containers
    - "Sidecar" container pattern, where the "sidecar" container used to send metrics/logs to other destinations (seperation of concerns)

![](2022-04-20-10-55-30.png)