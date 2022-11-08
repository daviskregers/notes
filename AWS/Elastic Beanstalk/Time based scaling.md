---
Created: 2018-11-29 08:15:46
Modified: Monday 7th November 2022 07:09:17
Type: misc
Source: 
Tags: [development/aws/elastic-beanstalk]
---

# Time based scaling

It is available to add time events to change the default scaling configuration in the `ELB Configuration -> Capacity`.

Things worth to mention:

1. The events work only one way - once the event has ended, it won't revert the changes made. If you need to change scaling at a specific time and then revert it - you will need to create **2 separate events**.

2. Make sure to provide the dates in `UTC+0000` time not local time zone.

3. The `Recurrence` parameter - when the event will be triggered.

4. `Start time` and `End time` shows from what time to what time the event will be considered active (will trigger cron). 