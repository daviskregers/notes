# Route 53 - Health Checks

- HTTP Health Checks are only for public resources
- Health Check => Automated DNS Failover
    - Health checks that monitor an endpoint (application, server, other AWS resource)
    - Health checks that monitor other health checks (Calculated Health Checks)
    - Health checks that monitor CloudWatch alarms (full control) - e.g. throttles of dynamodb, alarms on RDS, custom metrics (helpful for private resources)

- Health Checks are integrated with CloudWatch metrics

## Monitoring an Endpoint

- About 15 global health checkers will check the endpoint health
    - Health/Unhealthy threshold - 3 (default)
    - Interval - 30 seconds (can set up to 10 seconds - higher cost)
    - Supported protocols: HTTP, HTTPS, TCP
    - If > 18% of health checkers report the endpoint is healthy, route 53 considers it healthy. Otherwise, it's unhealthy.
    - Ability to choose which locations you want route 53 to use.
- Health Checks pass only when the endpoint responds with 2xx or 3xx status codes
- Health Checks can be set up to pass / fail basedon the test in the first 5120 bytes of the response
- Configure your router/firewall to allo incoming requests from  route 53 health checkers

## Calculated Health Checks

- Combine the results of multiple checks into a single health check
- You can use OR, AND or NOT
- Can monitor up to 256 Child Health Checks
- Specify how many of the health checks need to pass to make the parent class
- Usage: perform maintenance to your website without causing all health checks to fail

## Health Check - Private Hosted Zones

- Route 53 Health checkers are outside the VPC
- They can't access private endpoints (private VPC or on-premises resources)
- You can create a CloudWatch metric and associate CloudWatch Alarm, then create a Health Check that checks the alarm itself.

