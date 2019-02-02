# Overview

In this section we'll build a docker image, that serves an application for counting number of times a webpage has been visited.
The application will consist of 2 servers - node.js application and redis.

We will have separate node app servers that connects to the redis server so later on it could be scaled up properly.