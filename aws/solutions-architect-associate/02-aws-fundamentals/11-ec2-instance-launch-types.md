# EC2 Instance Launch Types

- On Demand Instances
    - Pay for what you use (billing per second, after the first minute)
    - Has higher cost but no upfront payment
    - No long term commitment
    - Recommended for short-term and un-interrupted workloads, where you can't predict how the application will behave.
- Reserved instances
    - Up to 75% discount compared to On-demand
    - Pay upfront for what you use with long term commitment
    - Reservation period can be 1 or 3 years
    - Reserve a specific instance type
    - Recommended for steady state usage applications (like databases)
- Covertible Reserved Instances 
    - can change the EC2 instance type
    - Up to 54% discount
- Scheduled Reserved Instances 
    - launch within time window you reserve
- Spot instances - short workloads, for cheap, can lose instances
    - Can get a discount of up to 90% compared to On-demand
    - You bid a price and get the instance as long as it's price is under the price
    - Price varies on offer and demand
    - Spot instances are reclaimed with a 2 minute notification warning when the spot price goes above your bid
    - Used for batch jobs, Big Data analysis, or workloads that are resilient to failures.
    - Not great for critical jobs or databases.
- Dedicated instances
    - Instances running on hardware that's dedicated to you
    - May share hardware with other instances in same account
    - No control over instance placement (can move hardware after Stop / Start)
- Dedicated Hosts 
    - Physical dedicated EC2 server for your use
    - Full controll of EC2 instance placement
    - Visibility into the underlying sockets / physical cores of the hardware
    - Allocated for you account for a 3 year period reservation
    - More expensive
    - Useful for software that have complicated licensing model (BYOL - Bring Your Own License)
    - Or for companies that have strong regulatory or compliance needs

## Hands on

When viewing EC2 instances on the left sidebar, we have a list of these types available.

![](../../../images/2019-11-22-12-35-14.png)

Then, we can search for a reserved instance with a term of 12 months and payment upfront.

![](../../../images/2019-11-22-12-36-55.png)

Similar process goes for all the other types.

For spot instances, we can click on launch an instance and in the configuration, set settings for it.

![](../../../images/2019-11-22-12-39-59.png)

Same goes with dedicated hardware, we can select that in the same form.

![](../../../images/2019-11-22-12-40-52.png)

## Deep Dive

- R - applications that need a lot of RAM - in-memory caches
- C - applications that needs good CPU - compute / databases
- M - applications that are balanced - general / web app
- I - applications that needs good local I/O - storage
- G - applications that need a GPU - video rendering / machine learning
- T2 / T3 - burstable instaces 
    - AWS has the concept of burstable instances
    - Burst means that overall, the instance has OK CPU performance
    - When the machine needs to process something unexpected (a spike in load for example), it can burst, and CPU can be VERY good.
    - If the machine bursts, it utilizes "burst credits"
    - If all the credits are gone, the CPU becomes bad
    - If the machine stops bursting, credits are accumulated over time
    - Amazin to handle unexpected traffic and getting the instance that it will handle it correctly
    - If your instance consistently runs low on credit, you need to move to a different kind of non-burstable instance
    
- T2 / T3 - unlimited
    - It is possible to have an unlimited burst credit balance
    - You pay extra money if you go over your credit balance, but you don't lose performance
    - Overall, it is a new offering, so be careful, costs could go high if you're not monitoring the health of your instances

![](../../../images/2019-11-22-12-47-21.png)

![](../../../images/2019-11-22-12-47-46.png)

We can see all the instance types available at [https://ec2instances.info/](https://ec2instances.info/).

