# Introducting docker compose

We have built a node.js server that relies on redis in order to work. If we start it up now, it will fail because it cannot connect to redis. Even if we run a `docker run redis`, it will not work because they are separate services and cannot talk to each other.

We need to setup networking between them. This can be achieved either by using docker CLI's networking features or using docker compose.

Docker compose is a separate tool that:
1. Used to start up multiple docker containers at the same time
2. Automates some of the long-winded arguments we were passing to `docker run`.

