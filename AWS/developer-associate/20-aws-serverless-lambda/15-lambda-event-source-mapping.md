# Lambda Event Source Mapping

- Kinesis Data Streams
- SQS & SQS FIFO queue
- DynamoDB Streams

- Common denominator: records need to be polled from the source
- You Lambda function is invoked synchonously

![](2022-05-12-07-55-32.png)

## Streams & Lambda (Kinesis & DynamoDB)

- An event source mapping creates an iterator for each shard, processes items in order
- Start with new items, from the beginning or from timestamp
- Processed items aren't removed from the stream (other consumers can read them)
- Low traffic: use batch window to accumulate records before processing
- You can process multiple batches in parallel
    - Up to 10 batches per shard
    - in-order processing is still guaranteed for each partition key

![](2022-05-12-07-57-40.png)

https://aws.amazon.com/blogs/compute/new-aws-lambda-scaling-controls-for-kinesis-and-dynamodb-event-sources/

## Streams & Lambda - Error Handling

- By default, if your function returns an error, the entire batch is reprocessed until the function suceeds, or the items in the batch expire.
- To ensure in-order processing, processing for the affected shard is paused until error is resolved.
- You can configure the event source mapping to:
    - discard old events
    - restrict the number of retries
    - split the batch on error (to work around Lambda timeout issues)
- Discarded events can go to a Destination

## Lambda - Event Soutce Mapping

### SQS & SQS FIFO

- Event Source Mapping will poll SQS (Long Polling)
- Specify batch size (1-10 messages)
- Recommended: Set the queue visibility timeout to 6x the timeout of your Lambda function
- To use a DLQ
    - Set up the SQS queue, not Lambda (DLQ for Lambda is only for async invocations)

![](2022-05-12-08-01-51.png)

## Queues & Lambda

- Lambda also supports in-order processing for FIFO (first-in, first-out) queues, **scaling up to the number of active message groups**.
- For standard queues, items aren't necessarily processed in order.
- Lambda scales up to process a standard queue as quickly as possible.

- When an error occurs, batches are returned to a queue as individual items and might be processed in a different grouping than the original batch.
- Ocassionaly, the event source mapping might receive the same item from the queue twice, even if no function error ocurred.
- Lambda deletes items from the queue after they're processed successfully.
- You can configure the source queue to send items to a dead-letter queue if they can't be processed.

## Lambda Event Mapper Scaling

- Kinesis Data Streams & DynamoDB Streams
    - One Lambda invocation per stream shard
    - If you use parallelization, up to 10 batches processed per shard simultaneously
- SQS Standard
    - Lambda adds 60 more instances per minute to scale up
    - Up to 1000 batches of messages processed simultaneously
- SQS FIFO
    - Messages with the same GroupID will be processed in order
    - The Lambda function scales to the number of active message groups

