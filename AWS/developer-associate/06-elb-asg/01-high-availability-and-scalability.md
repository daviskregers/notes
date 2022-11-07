# Scalability & High Availability

- Scalabiliy means that an application / system can handle greater loads by adapting.
- There are two kinds of scalability:
    - Vertical scalability
    - Horizontal scalability (elasticity)
- Scalability is linked but different to High Availability

## Vertical Scalability

- Vertical scalability means increasing the size of the instance.
- For example, your application runs on t2.micro, scaling that application vertically means running it on t2.large.
- Vertical scalability is very common for non distributed systems, such as database.
- RDS, ElastiCache are services that can scale vertically.
- There's usually a limit to gow much you can vertically scale (hardware limit).

## Horizontal Scalability

- Horizontal Scalability means increasing the number of instances / systems for your application.
- Horizontal scaling implies distributed systems.
- This is very common for web applications / modern applicaitons.
- It's easy to horizontally scale thanks to cloud offerings such as Amazon EC2.

## High Availability

- High Availability usually goes hand in hand with horizontal scaling
- High Availability means running your application / system in at least 2 data centers (Availability Zones)
- The goal of High Availability is to survive a data center loss
- The High Availability can be passive (for RDS Multi AZ for example).
- The High Availability can be active (for horizontal scaling).

## High Availability & Scalability for EC2

- Vertical Scaling: Increase instance size (scale up/down)
    - From: t2.namo - 0.5G RAM, 1 vCPU
    - To: u-l2tgb1.metal - 12.3TB RAM, 448 vCPUS

- Horizontal Scaling: Increase number of instances (scale in/out)
    - Auto Scaling Group
    - Load Balancer
- High Availability: Run instances for the same application across multi AZ
    - Auto Scaling Group multi AZ
    - Load Balancer multi AZ