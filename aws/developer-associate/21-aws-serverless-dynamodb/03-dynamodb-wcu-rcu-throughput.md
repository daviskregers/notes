# DynamoDB - Write Capacity Units & Read Capacity Units - Throughput

## Read/Write Capacity Modes

- Control how you manage your table's capacity (read/write throughput)
- Provisioned mode (default)
    - You specify the number of reads/writes per second
    - You need to plan capacity beforehand
    - Pay for provisioned read & write capacity units
- On-Demand Mode
    - Read/writes automatically scale up/down with your workloads
    - No capacity planning needed
    - Pay for what you use, more expensive ($$$)
- You can switch between different modes once every 24 hours

## R/W Capacity Modes - Provisioned

- Table must have provisioned read and write capacity units
- Read Capacity Units (RCU) - throughput for reads
- Write Capacity Units (RCU) - throughput for writes
- Option to setup auto-scaling of throughput to meet demand
- Throughput can be exceeded temporarily using "Burst Capacity"
- If Burst Capacity has been consumed, you'll get a "ProvisionedThroughputExceededException"
- It's when advised to do an exponential backoff retry.

## DynamoDB - Write Capacity Units (WCU)

- One Write Capacity Unit (WCU) represents one write per second for an item up to 1 KB in size
- If the items are larger than 1KB, more WCUs are consumed

- Example 1: we write 10 items per second, with item size of 2KB
    - We need 10 * (2KB / 1 KB) = 20 WCUs
- Example 2: we write 6 items per second with item size 4.5KB
    - We need 6 * (5KB / 1KB) = 30 WCUs (we round up 4.5KB to 5KB)
- Example 3: we write 120 items per minute, with item size of 2KB
    - We need (120 / 60) * (2KB / 1KB) = 4 WCUs

## Strongly Consistent Read vs Eventually Consistent Read
- Eventually Consistent Read (default)
    - If we read just after a write, it's possible we'll get some stale data because of replication.
- Strongly Consistent Read
    - If we read just after a write, we will get the correct data
    - Set "ConsistendtRead" parameter to True in API calls (GetItem, BatchGetItem, Query, Scan)
    - Consumes twice the RCU

![](2022-05-17-07-06-00.png)

## DynamoDB - Read Capacity Units (RCU)

- One Read Capacity Unit (RCU) represents one Strongly Consistent Read per second or two Eventually Consistent Reads per second, for an item up to 4 KB in size. If the items are larger than 4KB, more RCUs are consumed.

- Example 1: 10 Strongly Consistent Reads per second, with item size 4 KB
    - We need 10 * (4KB/4KB) = 10 RCUs
- Example 2: 16 Eventually Consistent Reads per second, with item size 12 KB
    - We need (16 / 2) * (12 KB / 4 KB) = 24 RCUs
- Example 3: 10 Strongly Consistent Reads per second, with item size 6KB
    - We need 10 * (8KB / 4 KB) = 20 RCUs (we must round up 6KB to 8KB)

## DynamoDB - Partitions Internal

- Data is stored in partitions
- Partition Keys go through a hashing algorithm to know which partition they go to
- To compute the number of partitions:
    - \# of partitionsByCapacity = (RCUsTotal / 3000) + (WCUsTotal/1000)
    - \# of partitionsBySize = TotalSize / 10GB
    - \# of partitions = ceil(max(\# of partitionsByCapacity, \# of partitionsBySize))

- WCUs and RCUs are spread evenly across partitions.

![](2022-05-17-07-12-47.png)

## DynamoDB - Throttling

- If we exceed provisioned RCUs or WCUs, we get "ProvisionedThroughputExceededException"
- Reasons:
    - Hot Keys - one partition key is being read too many times (e.g., popular item)
    - Hot partitions
    - Very large items, remember RCU and WCU depends on size of items
- Solutions
    - Exponential backoff when exception is encountered (already in SDK)
    - Distribute partition keys as much as possible
    - If RCU issue, we can use DynamoDB Accelerator (DAX)

## R/W Capacity Modes - On Demand

- Read/writes automatically scale up/down with your workloads
- No capacity planning needed (WCU/RCU)
- Unlimited WCU&RCU, no throttle, more expensive
- You're charged for reads/writes that you use in terms of RRU, WRU
- Read Request Units (RRU) - throughput for reads (same as RCU)
- Write Request Units (WRU) - thoughput for writes (same as WCU)
- 2.5x more expensive than provisioned capacity (use with care)
- Use cases: unknown workloads, unpredictable application traffic, ...