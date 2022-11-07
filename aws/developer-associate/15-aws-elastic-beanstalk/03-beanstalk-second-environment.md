# Creating a second environment

If we were to create new environment, it will ask us to choose the tier we want to use:

- Web Server environment
- Worker environment

![](2022-04-20-13-02-36.png)

While creating, we are are going to use the `Configure more options`.

Here, we'll have multiple presets available:

![](2022-04-20-13-04-32.png)

Also, there will be an option to configure everything related to the beanstalk

We can configure:
- Software
    - X-Ray daemon
    - S3 log storage
    - Instance log streaming to CloudWatch logs
    - Environment Properties
- Instances:
    - Root volume type
    - Security groups
- Capacity
    - Single / Load balanced environment type
    - Auto Scaling Group configuration
    - instance Type
    - AZs
    - Placement
    - Scaling triggers
- Load Balancer
    - Load balancer type (Application LB, Classic LB, network LB)
    - Listeners
    - Rules
    - Access Log file
    - You cannot change the load balancer once the environment is created
- Rolling Updates & Deployments
- Security
    - Service role
    - Keypairs
- Monitoring
- Managed updates
- Notifications
- Networking
- Databases
    - if you create an RDS through this, when deleting the environment it will delete it as well.
- Tags