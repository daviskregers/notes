# CloudWatch Alarms

- Alarms are used to trigger notifications for any metric
- Various options (sampling, %, max, min, etc...)
- Alarm states:
    - OK
    - INSUFFICIENT_DATA
    - ALARM
- Period:
    - Length of time in seconds to evaluate the metric
    - High resolution custom metrics: 10 sec, 30 sec or multiples of 60 sec

## Alarm Targets

- Stop, Terminate, Reboot or Recover an EC2 instance (EC2)
- Trigger Auto Scaling Action (EC2 AutoScaling)
- Send notification to SNS (from which you can do pretty much anything)

## Instance Recovery

- Status Check:
    - Instance status = check the EC2 VM
    - System status = check the underlying hardware
- Recovery: Same private, public, elastic IP, metadata, placement group

![](2022-04-26-10-01-51.png)

## Good to Know

- Alarms can be created based on CloudWatch Logs Metrics Filters

![](2022-04-26-10-03-12.png)

- To test alarms and notifications, set the alarm state to Alarm using CLI

```console
$ aws cloudwatch set-alarm-state --alarm-name "myalarm" --state-value ALARM --state-reason "testing purposes"
```