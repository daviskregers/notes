# Monitoring Overview in AWS

## Why is monitoring important

- We know how to deploy applications
    - Safely
    - Automatically
    - Using IaC
    - Leveraging best AWS components
- Our applications are deployed, and our users don't care how we did it.
- Our users only care that the application is working
    - Application latency: will it increase over time?
    - Application outages: customer experience should not be degraded
    - Users contacting the IT department or complaining is not a good outcome
    - Troubleshooting and remediation
- Internal monitoring
    - Can we prevent issues before they happen?
    - Performance and cost
    - Trends (scalling patterns)
    - Learning and improvement

## Monitoring in AWS

- CloudWatch
    - Metrics: Collect and track key metrics
    - Logs: Collect, monitor, analyize and store log files
    - Events: Send notifications when certain events happen in your AWS
    - Alarms: React in real-time to metrics / events
- AWS X-Ray:
    - Troubleshooting application performance and errors
    - Distributed tracing of microservices
- AWS CloudTrail
    - Internal monitoring of API calls being made
    - Audit changes to AWS Resources by your users