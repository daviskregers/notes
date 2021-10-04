# Auto Scaling Groups - Scaling Policies

## Dynamic Scaling Policies
- Target Tracking Scaling
    - Most simple and easy to set-up
    - Example: I want the average ASG CPU to stay at around 40%
- Simple / Step Scaling
    - When a CloudWatch alarm is triggered (example CPU > 70%) - add 2 units.
    - When a CloudWatch alarm is triggered (example CPU < 30%), then remove 1 unit
- Scheduled Actions
    - Anticipate a scaling based on known usage patterns
    - Example: increase the min capacity to 10 at 5pm on Fridays

## Predictive Scaling

- Continuously forecast load and schedule scaling ahead
    - Analyze historical load
    - Generate forecast
    - Schedule scaling actions

## Good metrics to scale on

- CPUUtilization: Average CPU utilization across your instances
- RequestCountPerTarget: to make sure the number of requests per EC2 isntances is stable
- Average Network In / Out (if your application is network bound)
- Any custom metric (that you push using CloudWatch)

## Scaling Cooldowns

- After a scaling activity happens, you are in the cooldown period (default 300 seconds)
- During the cooldown period, the ASG will not launch or terminate additional instances (to allow for metrics to stabilize)
- Advice: Use a ready-to-use AMI to redice configuration time in order to be service requests faster and reduce the cooldown period

