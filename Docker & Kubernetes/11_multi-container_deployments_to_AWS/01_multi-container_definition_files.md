# Multi-container definition files

Previously when we deployed to AWS, we had a single Docker image to be ran. Now we have multiple images and we'll need to specify what exactly we need to do.

We'll need to create a `Dockerrun.aws.json` file, where we'll make container definitions, which is similar to `docker-compose.yml` file.

----

The Elastic Beanstalk doesn't really know on how to run containers itself, whenever it needs to do so, it delegates it to `Amazon Elastic Container Service (ECS)`. 

The Parameters on how to create the `Dockerrun.aws.json` file can be found here [https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definition_parameters.html](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definition_parameters.html).

----

So, we'll create `Dockerrun.aws.json` file in the project directory:

```json
{
    "AWSEBDockerrunVersion": 2,
    "containerDefinitions": [
        {
            "name": "client",
            "image": "deiveris/multi-client",
            "hostname": "client",
            "essential": false,
        },
        {
            "name": "server",
            "image": "deiveris/multi-server",
            "hostname": "api",
            "essential": false
        }, 
        {
            "name": "worker",
            "image": "deiveris/multi-worker",
            "hostname": "worker",
            "essential": false
        },
        {
            "name": "nginx",
            "image": "deiveris/multi-nginx",
            "hostname": "nginx",
            "essential": true,
            "portMappings": [
                {
                    "hostPort": 80,
                    "containerPort": 80
                }
            ],
            "links": ["client", "server"]
        }
    ]
}
```

The `essential` marks the container to be essential, meaning when it crashes - all other containers are closed down as well. At least 1 container must be marked as essential.

