# MySQL scaling

## Methods

The process and methods of scaling are categorized into several categories:

### Vertical Scaling or Scale-up

In vertical scaling, we increase the CPU, RAM and Storage or but a more robust server in order to support more traffic and load on our database server.

**Pros**

1. Less power consumption than running multiple servers
2. Colling costs are less than scaling horizontally
3. Generally less challenges to implement
4. Less licensing costs (if using paid databases)

**Cons**

1. It's way more costly
2. There is a limit to increasing hardware on a single system
3. Greater risk of hardware failure causing bigger outages

### Horizontal Scaling or Scaling-out

In horizontal scaling we add more systems with smaller configuration in terms of CPU, RAM and storage to distribute the traffic or load across these systems.

**Pros**

1. Much cheaper than scaling vertically
2. Easier to run fault-tolerance
3. Easy to upgrade

**Cons**

1. Bigger footprint on data centre
2. Higher utility cost
3. More licensing fees (if using paid databases)

When we use the Vertical and Horizontal scaling at the same time, we call it the `Hybrid Scaling` approach.

## Scaling MySQL database

By default, the MySQL can be scaled either by using vertical or hybrid approaches, but not fully horizontal approach.

## Master-slave approach

Generally, we tend to create a `Master-Slave` architecture and route all the write queries on the master instance and all the read queries on the slave instances which are replicated from the `Master`. We can have multiple Slave instances running at one and scale our read operations horizontally. But the Master can only be scaled Vertically.

** Problems with the Master-Slave approach**

Every record inserted in MySQL tables have one primary key to index the records for faster select operations. Generally, we have `mysql_insert_id` as our primary key on the table, when having multiple masters, this key will be duplicated accross the databases and the data will be redundant to use.

In order to solve the duplicate ID issue, we can have one ID generator which generates the unique IDs and we can use the same ID as our primary key, but this will add one extra point of failure in the system due to concurrency. If the ID generator is down or slow, the whole database will fail.

### Solutions and approaches

#### ID Generator

To solve the duplicate ID issue in multiple master architecture you can use an ID generator server which generates unique time-based serial hashes which can be used as a primary key in mysql table. 

#### Concurrency

To solve the concurrency issue you can use a pool of IDs stored in the cache of the ID generator. When a write request occurs - it takes a generated ID from the cache and uses it as the primary key.