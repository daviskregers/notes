# High Availability and Scalability

- Scalability means that an application / systen can handle greater loads by adapting.
- There are two kinds of scalability:
    - Vertical scalability
    - Horizontal scalability (= elasticity)

- Scalability is linked but different to High Availability

## Vertican Scalability

- Vertical scalability means increasing the size of the instance
- For example, your application runs on a t2.micro
- Scaling that application vertically means running it on t2.large
- Vertical scalability is very common for non distributed systems, such as a database.
- RDS, ElastiCache are services that can scale vertically.
- There's usually a limit to how much you can vertically scale (hardware limit)

## Horizontal Scalability

- Horizontal Scalability means increasing the number of instances / systems for your application
- Horizontal scaling implies distributed systems
This is very common for web applications / modern applications
- It's easy to horizontally scale thanks to the cloud offerings such as Amazon EC2

## High Availability

- High availability usually goes hand in hand with horizontal scalin
- High availability means running your application /system in at least 2 data centers (AZs)
- The goal of high availability is to survive a data center loss
- The high availability can be passive (for RDS Multi AZ for example)
- The high availability can be active (for horizontal scaling)

## High Availability & Scalability for EC2

- Vertical Scaling: Increase instance size (= scale up/down)
    - From: t2.nano - 0.5G of ram, 1 vCPU
    - To: u-12tb1.metal - 12.3TB of ram, 448 vCPUs
- Horizontal scaling: increase number of isntances (= scale out/in)
    - Auto Scaling Group
    - Load Balancer
- High Availability: Run instances for the same application across multi AZ
    - Auto Scaling Group multi AZ
    - Load Balancer multi AZ