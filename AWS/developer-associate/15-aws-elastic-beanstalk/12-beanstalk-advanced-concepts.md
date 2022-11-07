# Beanstalk Advanced Concepts

## Beanstalk with HTTPS
- Idea: Load the SSL certificate onto the Load Balancer
- Can be done from the Console (EB Console, load balancer configuration)
- Can be done from the code: .ebextensions/securelistener-alb.config
- SSL Certificate can be provisioned using ACM (AWS Certificate Manager) or CLI
- Must configure a security group rule to allow incoming port 443 (HTTPS port)
- Beanstalk redirect HTTP to HTTPS
    - Configure your instances to redirect HTTP to HTTPS:
        - https://github.com/awsdocs/elastic-beanstalk-samples/tree/master/configuration-files/aws-provided/security-configuration/https-redirect
    - OR configure the Application Load Balancer (ALB only) with a rule
    - Make sure health checks are not redirected (so they keep giving 200 OK)

## Web Server vs Worker Environment

- If your application performs tasks that are long to complete, offload these tasks to a dedicated worker environment
- Decoupling your application into two tiers is common
- Example: processing a video, generating a zip file, etc
- You can define periodic tasks in a file cron.yaml

## Custom Platform (Advanced)

- Custom Platforms are very advanced, they allow to define from scratch:
    - The Operating System (OS)
    - Additional Software
    - Scripts that Beanstalk runs on these platforms
- Use case: app language is incompatible with Beanstalk & doesn't use Docker
- To create your own platform:
    - Define an AMI using Platform.yaml file
    - Build that platform using the Packer software (open source tool to create AMIs)
- Custom Platform vs Custom Image (AMI)
    - Custom Image is to tweak an existing Beanstalk Platform (python, node.js, java)
    - Custom platform is to create an entirely new Beanstalk Platform