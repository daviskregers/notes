# Application architecture

We will create an application for fibonacci calculator.

It will consist of multiple containers:
- Nginx - routing, decides whether browser wants to access the react or express (API) server
  - React server
  - Express (API) server 
    - Redis server -  caches indices submitted.
      - Worker - watches redis for new indicies, whenever a new value shows up - calculates and puts back into redis.
    - Postgres server - stores indices submitted.

