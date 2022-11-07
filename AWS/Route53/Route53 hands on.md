---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/rds/route53, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# Route53 hands on

You can navigate to `Route 53` via your AWS console. 
There we can `Register domain` if you wish to buy a domain, we can also transfer already owned domains.

When opening up hosted zone from a domain, we can setup it's DNS records.

![](2019-12-30-10-05-25.png)

## EC2 Setup

We can create an EC2 instances in multiple AZs, create an Application Load Balancer for them, then create an alias in the Route 53 to the Load Balancer.

## TTL

In order not to overload the DNS, we use TTL to cache the DNS response for the provided duration. If the IP address of the server would change not all of the clients would see the change before the TTL expires.

The TTL can be set when creating records:

![](2019-12-30-10-11-38.png)

## CNAME vs ALIAS

AWS Resources (Load Balancer, CloudFront etc) expose an AWS URL (lb1-1234.us-east-2.elb.amazonaws.com) and you want it to be myapp.mydomain.com
- CNAME:
    - Points a URL to any other URL. (app.mydomain.com => xyz.anything.com)
- Alias
    - Points a URL to AWS resource (app.mydomain.com => xyz.amazonaws.com)
    - Works for root domain and non-root domain
    - Free of charge
    - native health checks

So, for subdomains we can create both CNAME and ALIAS for our load balancer, but alias would be the recommended way to go. For root domain, we can only use ALIAS.

![](2019-12-30-10-16-01.png)

## Routing Policy - Simple

- Maps a domain to one URL
- Use when you need to redirect to a single resource
- You can't attach health checks to simple routing policy
- If multiple values are returned, a random one is chosed by the client

## Routing Policy - Weighted

- Control the % of the requests that go to specific endpoint
- Helpful to test 1% of traffic on new app version for example
- Helpful to split traffic between two regions
- Can be associated with health checks

We can create multiple records with the same name and attach different weights:

![](2019-12-30-10-22-19.png)

## Routing Policy - Latency

- Redirect to the server that has least latency close to us
- Super helpful when latency of users is a priority
- Latency is evaluated in terms of user to designated AWS Region
- Germany may be directed to the US (if that's the lowest latency)

Same as the weighted policy, we can create multiple rules and attach different regions.

![](2019-12-30-10-24-19.png)

## Route 53 Health Checks

- If we have X health checks failed, we mark resource as unhealthy (default 3)
- After X health checks passed, mark as healthy (default 3)
- Default Health Check interval: 30 seconds (can set up to 10s - higher cost)
- About 15 health checkers will check the endpoint health
- One request every 2 seconds on average
- Can have HTTP, TCP and HTTPS health checks (no SSL verification)
- Possibility of integrating the health check with CloudWatch

- Health checks can be linked to Route53 DNS queries.

![](2019-12-30-10-28-13.png)

![](2019-12-30-10-29-14.png)

## Routing Policy - Failover

We can have 2 EC2 instances and route between them based on health checks. If the primary instance is unhealthy, route client to secondary one for disaster recovery.

## Routing Policy - GeoLocation

- Different from Latency based
- This is routing based on user location
- Here we specify traffic from the UK should go to this specific IP
- Should create a default policy (in case there's no match on location)

![](2019-12-30-10-34-18.png)

## Routing Policy - Multi Value

- Use when routing traffic to multiple resources
- Want to associate a route 53 with records
- Up to 8 healthy records are returned for each Multi Value query
- Multi Value is not substutute for having an ELB

## Route53 as a Registrar

A domain name registrar is an organization that manages the reservation of internet domain names like GoDaddy, Google Domains and also Route 53.

But, if you buy a domain from a 3rd party, you can still use Route 53.

- Create A Hosted Zone in Route 53.
- Update NS Records on 3rd party to use Route 53 name servers.
- 