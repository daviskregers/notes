# CodeDeploy for EC2 and ASG

- Define how to deploy the application using appspec.yml + Deployment Strategy
- Will do In-place update to your fleet of EC2 instances
- Can use hooks to verify the deployment after each deployment phase

## Deploy to an ASG

- In-place Deployment
    - Updates existing EC2 instances
    - Newly created EC2 instances by an ASG will also get automated deployments
- Blue / Green Deployment
    - A new Auto-Scaling Group is created (settings are copied)
    - Choose how long to keep the old EC2 instances (old ASG)
    - Must be using an ELB

## Redeploy & Rollbacks

- Rollback = redeploy a previously deployed revision of your application
- Deployments can be rolled back:
    - Automatically - rollback when a deployment fails or rollback when a CloudWatch Alarm thresholds are met
    - Manually
- Disable Rollbacks - do not perform rollbacks for this deployment
- If a roll back happens, CodeDeploy redeploys the last known good revision as a new deployment (not a restored version)

