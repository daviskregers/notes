# Kinesis Producers

- Puts data records into data streams
- Data record consists of:
    - Sequence number (unique per partition-key within shard)
    - Partition key (must specify while put records into stream)
    - Data blob (up to 1 MB)
- Producers:
    - AWS SDK: simple producer
    - Kinesis Producer Library (KPL): C++, Java, batch, compression, retries
    - Kinesis agent: monitor log files
- Write throughput: 1MB/s or 1000 records/s per shard
- PutRecord API
- Use batching with PutRecords API to reduce costs & increase throughput

![](2022-04-27-07-44-12.png)

## ProvisionedThroughputExceeded

- Use highly distributed partition key
- Retries with exponential backoff
- Increase shards (scaling)

![](2022-04-27-07-45-53.png)