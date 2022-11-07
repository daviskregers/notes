# Stateless Web App: WhatIsTheTime.com

- WhatIsTheTime.com allows people to know what time it is
- We don't need a database
- We want to start small and can accept downtime
- We want to fully scale vertically and horizontally, no downtime
- Let's go through the Solutions Architect journey for this app

## Starting simple

- Create a single t2.micro instance

## Scaling vertically 

- When we have more traffic for the t2.micro instance to handle, we scale it vertically to something like m5.large.
- Downtime while upgrading to new instance.

## Scaling horizontally

- Instead of scaling vertically, we can add multiple instances to balance the load between them.
- In one instance goes away, we can leverage Load Balancer and health checks to route clients to a different instance.
- We can use auto-scaling group to manage the instance count automatically
- In order to make our app disaster tolerant, we can also make it multi AZ.