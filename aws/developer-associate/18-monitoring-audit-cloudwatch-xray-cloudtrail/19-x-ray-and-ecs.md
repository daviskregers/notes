# X-Ray and ECS

![](img/2022-04-26-17-57-13.png)

## Example task definition

```json
{
    "name": "xray-daemon",
    "image": "123456789012.dkr.ecr.us-east-2.amazonaws.com/xray-daemon",
    "cpu": 32,
    "memoryReservation": 256,
    "portMappings": [
        {
            "hostPort": 0,
            "containerPort": 2000,
            "protocol": "udp"
        }
    ]
},
{
    "name": "scorekeep-api",
    "image": "123456789012.dkr.ecr.us-east-2.amazonaws.com/scorekeep-api",
    "cpu": 192,
    "memoryReservation": 512,
    "environment": [
        { "name": "AWS_REGION", "value" : "us-east-2" },
        { "name": "NOTIFICATION_TOPIC", "value" : "arn:aws:sns..." },
        { "name": "AWS_XRAY_DAEMON_ADDRESS", "value" : "xray-daemon:2000" }
    ],
    "portMappings": [
        {
            "hostPort": 5000,
            "containerPort": 5000,
        }
    ],
    "links": [
        "xray-daemon"
    ]
}
```

https://docs.aws.amazon.com/xray/latest/devguide/xray-daemon-ecs.html#xray-daemon-ecs-build

