# Network Load Balancer (NLB)

- Network load balancers (layer 4) allow to:
    - Forward TCP & UDP traffic to your instances
    - Handle millions of requests per second
    - Less latency ~ 100ms (vs 400ms for ALB)
- NLB has one static IP per AZ, and supports assigning Elastic IP (helpful for whitelisting specific IP)
- NLB are used for extreme performance, TCP or UDP traffic
- Not included in the AWS free tier

