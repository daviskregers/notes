---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/kinesis, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

## Hands on

Visit [[Kinesis]] from [[AWS Console]].

![](2019-12-31-11-09-32.png)

![](2019-12-31-11-09-47.png)

Create a data stream.

![](2019-12-31-11-14-14.png)

Then you can work with it using the CLI.

```
$ aws kinesis help
$ aws kinesis list-streams help
$ aws kinesis list-streams
{
    "StreamNames": [
        "my-first-stream"
    ]
}
$ aws kinesis describe-stream help
$ aws kinesis describe-stream --stream-name my-first-stream
{...}
$ aws kinesis put-record --stream-name my-first-stream --data "user signup" --partition-key user_123
{
    "ShardId": "shardId-00000000000",
    "SequenceNumber": "4958877456415503463748463555080986096182857601881824546"
}
$ aws kinesis get-shard-iterator --stream-name my-first-stream --shard-id shardId-00000000000 --shard-iterator-type TRIM_HORIZON
{
    "ShardIterator": "..."
}
$ aws kinesis get-records help
$ aws kinesis get-records --shard-iterator "..." 
{
    "Records": [
        {
            "SequenceNumber": "4955877456415503463...",
            "AppriximateArrivalTImestamp": 1538394164.478,
            "Data": "dXNlciBzaWdudXa=", // base64 encoded
            "PartitionKey": "user_123"
        },
        ...
    ],
    "NextShardIterator": "AAA...",
    "MillisBehindLatest": 0
}
```
