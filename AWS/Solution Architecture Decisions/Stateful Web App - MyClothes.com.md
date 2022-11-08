---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/architecture, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# Stateful Web App: MyClothes.com

- MyClothes.com allows people to buy clothes online.
- Theres a shopping cart
- Our website is having hundreds of users at the same time
- We need to scale, maintain horizontal scalability and keep our web application as stateless as possible
- Users should not lose their shopping cart
- Users should have their details (address, etc) in a database

We can use Multi AZ setup with a Load Balancer, auto scaling group.

There are multiple ways to keep the sessions:
- Use load balancer stickiness
    - Each instance saves the session
    - In order to keep it, we need to route user to the same instance
    - Can create load disbalance
- Introduce user Cookies
    - Stateless
    - HTTP requests are heavier
    - Security risk (cookies can be altered)
    - Cookies must be validated
    - Cookies must be less than 4KB
- Store session data into ElastiCache or DynamoDB
    - Stateless
    - Multi AZ
    - Can also be used for caching data from RDS
    - Tighter security with security groups referencing each other
