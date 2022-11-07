# Elastic Load Balancer - Cross Zone Load Balancing

With Cross Zone Load Balancing:
- each load balancer instance distributes evenly across all registered instances in all AZ

Without Cross Zone Load Balancing:
- Requests are distributed in the instances of the node of the Elastic Load Balancer

Application Load Balancer:
- Always on (can't be disabled)
- No charges for inter AZ data

Network Load Balancer
- Disabled by default
- You pay charges ($) for inter AZ data if enabled

Classic Load Balancer
- Through Console - enabled by default
- Through CLI/API - disabled by default
- No charges for inter AZ data if enabled