# Kinesis Data Streams Consumers

- Get data records from data streams and process them

- AWS Lambda
- Kinesis Data Analytics
- Kinesis Data Firehose
- Custom Consumer (AWS SDK) - Classic or Enhanced Fan-Out
- Kinesis Client Library (KCL): library to simplify reading from data stream
- Custom Consumer
    - Shared (Classic) Fan-out Consumer
        - Low number of consuming applications
        - Read throughput: 2MB/s per shard across all consumers
        - Max: 5 GetRecords API calls/sec
        - Latency ~200ms
        - Minimize cost
        - Consumer poll data from Kinesis using GetRecords API call
        - Returns up to 10 MB (then throttle for 5 seconds) or up to 10000 records
    - Enhanced Fan-out Consumer
        - Multiple consuming applications for the same stream
        - 2MB/sec per consumer per shard
        - Latency ~70ms
        - Higher costs
        - Kinesis pushes data to consumers over HTTP/2 (SubscribeToShard API)
        - Soft limit of 5 consumer applications (KCL) per data stream (default)
- AWS Lambda
    - Supports Classic & Enhanced Fan-out consumers
    - Read records in batches
    - Can configure batch size and batch window
    - If error occurs, Lambda retries until succeeds or data expired
    - Can process up to 10 batches per shard simultaneously

![](2022-04-27-07-52-37.png)