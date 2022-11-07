# Kinesis Data Streams Hands On

![](2022-04-27-07-53-52.png)

![](2022-04-27-07-55-31.png)

```console
$ aws --version

# Producer for CLI v2
$ aws kinesis put-record --stream-name test --partition-key user1 --data "user signup" --cli-binary-format raw-in-base64-out

# Producer for CLI v1
$ aws kinesis put-record --stream-name test --partition-key user1 --data "user signup"

# Consumer

$ aws kinesis describe-stream --stream-name test

# We get the shard id from the describe and get a shard iterator next

$ aws kinesis get-shard-iterator --stream-name test --shard-id shardId-000000000 --shard-iterator-type TRIM_HORIZON

# next, we use the shard iterator to get the records

{
    "ShardIterator": "AAAAA...=="
}

$ aws kinesis get records --shard-iterator <iterator>

{
    "Records": [
        {
            "SequenceNumber": "123456",
            "ApproximateArrivalTimestamp": "...",
            "Data": "dXNlciBzaWdudXA=", # base64 encoded
            "PartitionKey": "user1"
        },
        ...
    ],
    "NextSharditerator": "AAAA...=="
}
```