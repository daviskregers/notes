# Route 53 - Routing Policies

- Define how Route 53 responds to DNS queries
- Don t get confused by the word "Routing"
    - It's not the same as Load Balancer routing which routes the traffic
    - DNS does not route any traffic, it only responds to DNS queries
- Route 53 supporrts the following routing policies
    - Simple
    - Weighted
    - Failover
    - Latency based
    - Geolocation
    - Multi-Value Answer
    - Geoproximity (using ROute 53 Traffic Flow feature)

## Simple Routing Policy

- Typically, route traffic to a single resource
- Can specify multiple values in the same record
- If multiple values are returned, a random one is chosen by the client
- When Alias is enabled, specify only one AWS resource
- Can't be associated with health checks