# What is serverless?

On traditional apps we might have a web app or a mobile app that needs a back-end REST API that hosts the business logic and provides data.

The REST API is made from a server written in a language like php, node, python, ruby etc.

As the traffic grows, we need to scale this server up and have multiple instances of it.

With this approach we have several issues:

1. We have to reinvent the wheel - we have to figure out the infrastructure
2. We have to figure out on how many servers we need, have a danger of under/over provisioning them.
3. We have to keep these servers updated, as we have to make sure we don't break everything.

We can use a special AWS service called `Lambda`, that executes code on demand, when it needs to run.

This provides the following:
1. The code is run on-demand
2. We don't have to pay any idle time
3. Service on creating APIs, don't have to create all that logic
4. Scales automatically
5. Code runs in up-to-date and secure environment

When using `lambda` we can use following languages:
- Node.js
- Java
- Python
- C#