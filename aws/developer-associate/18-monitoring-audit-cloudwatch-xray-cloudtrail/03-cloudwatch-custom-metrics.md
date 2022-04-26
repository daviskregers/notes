# CloudWatch Custom Metrics

- Possibility to define and send your own custom metrics to CloudWatch
- Example: memory (RAM) usage, disk space, number of logged in users
- Use API Call PutMetricData
- Ability to use dimensions (attributes) to segment metrics
    - Instance.id
    - Environment.name
- Metric resolution (StorageResolution API parameter - two possible values)
    - Standard: 1 minute (60 seconds)
    - High Resolution: 1/5/10/30 second(s) - Higher cost
- Important: Accepts metric data points two weeks in the past and two hours in the future (make sure to configure your EC2 instance time correctly)

```console
$ aws cloudwatch put-metric-data  --namespace "Usage Metrics" --metric data file://metric.json
```

```json
[
    {
        "MetricName": "New Posts",
        "TimeStamp": "Wednesday, June 12, 2013 8:28:20 PM",
        "Value": 0.50,
        "Unit": "Count"
    }
]
```

Specicify multiple dimensions

```console
$ aws cloudwatch put-metric-data --metric-name Buffers --name MyNameSpace --unit Bytes --value 231434333 --dimensions InstanceId=1-23456789,InstanceType=m1.small
```