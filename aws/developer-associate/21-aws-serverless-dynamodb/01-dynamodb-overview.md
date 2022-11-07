# DynamoDB Overview

## Traditional Architecture

![](2022-05-17-06-25-49.png)

- Traditional applications leverage RDBMS databases
- These databases have SQL query language
- Strong requirements about how the data should be modeled
- Ability to do query joins, aggregations, complex computations
- Vertical scaling (getting more powerful CPU / RAM / IO)
- Horizontal scaling (increasing reading capacity by adding EC2 / RDS Read Replicas)

## NoSQL databases

- NoSQL databases are non-relational databases and are distributed
- NoSQL databases include MongoDB, DynamoDB, ...
- NoSQL databases do not support query joins (or just limited support)
- All the data that is needed for a query is present in one row
- NoSQL databases don't perform aggregations such as SUM, AVG, ...
- NoSQL databases scale horizontally

- There's no "right or wrong" for NoSQL vs SQL, they just require to model the data differently and think about user queries differently.

## Amazon DynamoDB

- Fully managed, highly available with replication across multiple AZs
- NoSQL database - not a relational database
- Scales to massive workloads, distributed database
- Millions of requests per seconds, trillions of rows, 100s of TB of storage
- Fast and consistent in performance (low latency on retrieval)
- Integrated with IAM for security, authorization and administration
- Enables event driven programming with DynamoDB Streams
- Low cost and auto-scaling capabilities
- Standart & Infrequent Access (IA) Table Class

## DynamoDB - Basics

- DynamoDB is made of Tables
- Each table has a Primary Key (must be decided at creation time)
- Each table can have an infinite number of items (rows)
- Each item has attributes (can be added over time - can be null)
- Maximum size of an ittem - 400KB
- Data types supported are:
    - Scalar Types - String, Number, Binary, Boolean, Null
    - Document Types - List, Map
    - Set Types - String Set, Number Set, Binary Set

## DynamoDB - Primary Keys

- Option 1: Partition Key (HASH)
    - Partition key must be unique for each item
    - Partition key must be diverse so that the data is distributed
    - Example: user_id for a users table

![](2022-05-17-06-32-48.png)

- Option 2: Partition Key + Sort Key (HASH + Range)
    - The combination must be unique for each item
    - Data is grouped by partition key
    - Example: users-games table, user_id for partition key and game_id for sort key.

![](2022-05-17-06-34-16.png)

## Partition Keys - Excercise

- We're building a movie database
- What is the best partition key to maximize data distribution?
    - Movie_id
    - Producer_name
    - Leader_actor_name
    - Movie_language

- Movie_id has the highest cardinality so it's a good candidate
- Movie language doesn't take many values and may be skewed towards English so it's not a great choice for the partition key.