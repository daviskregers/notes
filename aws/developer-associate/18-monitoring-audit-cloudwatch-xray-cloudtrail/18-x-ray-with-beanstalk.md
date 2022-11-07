# X-Ray with Beanstalk

- AWS Elastic Beanstalk platforms include the X-Ray daemon
- You can run the daemon by setting an option in the Elastic Beanstalk console or with a configuration file (in .ebextensions/xray-daemon.config)

```yaml
option_settings:
    aws:elasticbeanstalk:xray:
        XRayEnabled: true
```

- Make sure to give your instance profile the correct IAM permissions so that the X-Ray daemon can function correctly.
- Then make sure your application code is instrumented with the X-Ray SDK
- Note: The X-Ray daemon is not provided for Multicontainer Docker

![](2022-04-26-17-55-43.png)

