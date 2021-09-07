# EC2 Instance Launch Types

## EC2 Instances Purchasing Options

- On-demand Instances: short workload, predictable pricing
- Reserved: minimum 1 year
    - Reserved Instances: long workloads
    - Convertible Reserved Instances: long workloads with flexible instances (can be converted to another size)
    - Scheduled Reserve Instances: example - every Thursday between 3 and 6pm
- Spot Instances: short workloads, cheap, can lose instances (less reliable)
- Dedicated Hosts: book an entire physical server, control instance placement

## EC2 on demand

- Pay for what you use:
    - Linux - billing per second, after the first minute
    - All other OSes - billing per hour
- Has the highest cost but no upfront payment
- No long-term commitment

Recommended for short-term and un-interrupted workloads, where you can't predict how the application will behave.

## EC2 Reserved Instances

- Up to 75% discount compared to on-demand
- Reservation period: 1 year = + discount | 3 years = +++ discount
- Purchasing options: no upfront | partial upfront = + | All upfront = ++ discount
- Reserve a specific instance type
- Recommended for steady-state usage applications (like databases)

---

- Convertible Reserved Instance
    - can change the EC2 instance type
    - Up to 54% discount
- Scheduled Reserved Instances
    - launch within time window you reserve
    - When you require a fraction of day / week / month
    - Still commitment over 1 to 3 years

## EC2 Spot Instances

- Can get a discount of up to 90% compared to on-demand
- Instances that you can "lose" at any point of time if your max price is less than the current spot price.
- The MOST cost-efficient instance in AWS
- Useful for workloads that are resilient to failure
    - Batch jobs
    - data analysis
    - Image processing
    - Any distributed workloads
    - Workloads with a flexible start and end time
- not suited for critical jobs or databases

## EC2 Dedicated Hosts

- An Amazon EC2 Decicated Host is a physical server with EC2 instance capability fully dedicated to your use. Dedicated Hosts can help you address compliance requirements and reduce costs by allowing you to use your existing server-bound software licenses.
- Allocated for your account for a 3-year period reservation.
- More expensive

- Useful for software that have complicated licensing model (BYOL - Bring Your Own License)
- Or for companies that have strong regulatory or compliance needs

## EC2 Dedicated Instances

- Instances running on hardware that's dedicated to you.
- May share hardware with other instances in same account.
- No control over instance placement (can move hardware after Stop/Start)