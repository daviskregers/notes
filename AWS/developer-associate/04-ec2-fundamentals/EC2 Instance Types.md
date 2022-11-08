# EC2 Instance Types Overview

You can use different types of EC2 instances that are optimized for different use cases: https://aws.amazon.com/ec2/instance-types/

Currently we have 7 different types of EC2 instances:
- General Purpose
- Compute Optimized
- Memory Optimized
- Accelerated Computing
- Storage Optimized
- Instance Features
- Measuring Instance Performance

Each of these types have a different set of families.

The AWS has the following naming convention like:
- m5.2xlarge
    - m: instance class
    - 5: generation (AWS Improves them over time)
    - 2xlarge: the size within the instance class. The more the size, the more the CPU, memory etc.

## EC2 Instance Types - General Purpose

- Great for a diversity of workloads such as web servers or code repositories.
- Balance between Compute, Memory, Networking.
- In this course, we will be using the t2.micro which is a General Purpose EC2 instance.

## EC2 Instance Types - Compute Optimized

- Great for compute-intensive tasks that require high performance processors:
    - Batch processing workloads
    - Media transcoding
    - High performance web servers
    - High performance computing (HPC)
    - Scientific modeling & machine learning
    - Dedicated gaming servers

## EC2 Instance Types - Memory Optimized

- Fast performance for workloads that process large data sets in memory.
- Use cases:
    - High performance, relational/non-relational databases
    - Distributed web scale cache stores
    - In-memory databases optimized for BI (Business Intelligence)
    - Applications performing real-time processing on big unstructured data

## EC2 Instance Types - Storage Optimized

- Great for storage-intensive tasks that require high, sequential read and write access to large data sets on local storage.
    - High frequency online transaction processing (OLTP) systems
    - Relationsl & NoSQL databases
    - Cache for in-memory databases (for example, Redis)
    - Data warehousing applications
    - Distributed file systems

---

There is a great resource https://instances.vantage.sh/ that lists all of the instance types and you can compare them.