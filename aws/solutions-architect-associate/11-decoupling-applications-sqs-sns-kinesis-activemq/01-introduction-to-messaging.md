# Introduction to Messaging

- When we start to deploying multiple applications, they will invevitably need to communicate with one another
- There are two patterns of application communication
    - Synchronous communications (application to application)
    - Asynchronous / Event based (application to queue to application)
- Synchronous between applications can be problematic if there are sudden spikes of traffic
- What if you need to suddenly encode 1000 videos but usually it's 10?
    - in that case it's better to decouple your applications
        - using SQS: queue model
        - using SNS: pub/sub model
        - using Kinesis: real-time streaming model
    - These services can scale independently from our application