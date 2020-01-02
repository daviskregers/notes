# Instantiating applications quickly

- When launching a full-stack (EC2, EBS, RDS), it can take time to:
    - Install applications
    - Insert initial (or recovery) data
    - Configure everything
    - Launch application
- We can take advantage of the cloud to speed that up.
- EC2 Instances
    - Use a Golden AMI: Install your appl;ications, OS dependencies etc before hand and launch your EC2 instance from the Golden AMI.
    - Bootstrap using User Data: For dynamic configuration, use user data scripts.
    - Hynrid: mix Golden AMI and User Data (Elastic Beanstalk).
- RDS Databases:
    - Restore from snapshot: the database will have schemas and data ready.
- EBS Volumes:
    - Restore from a snapshot: the disk will aready be formatted and have data.