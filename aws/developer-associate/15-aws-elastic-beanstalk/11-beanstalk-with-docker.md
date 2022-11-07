# Beanstalk with Docker

## Single DOcker

- Run your application as a single docker container
- Either provide:
    Dockerfile: Elastic Beanstalk will build and run the Docker container
    Dockerrun.aws.json (v1): Describe where *already built* docker image is:
    - Image
    - Ports
    - Volumes
    - Logging
    - Etc
- Beanstalk in Single Docker Container does not use ECS

## Multi Docker Container

- Multi Docker helps run multiple containers per EC2 instance in EB
- This will create for you:
    - ECS CLuster
    - EC2 Instance, configured to use the ECS Cluster
    - Load Balancer (in high availability mode)
    - Task definitions and execution
- Requires a config Dockerrun.aws.json (v2) at the root of source code
- Dockerrun.aws.json is used to generate the ECS task definition
- Your Docker images must be pre-built and stored in ECR for example

![](2022-04-20-12-22-31.png)

We can find sample configurations at: https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/tutorials.html