## Health Checks

- [[Health Checks]] are cruical for Load Balancers
- They enable the load balancer to know if instances it forwards traffic to are available to reply to requests
- The health check is done on a port and a route (/health is common)
- If the response is not 200 (OK), then the instance is unhealthy

![](../../../images/2019-11-22-14-08-13.png)

