# CodeBuild Hands On Part 1

When creating a CodeBuild project we have a ton of things to configure.

![](2022-04-21-08-53-26.png)

Here we can enable badges, restrict concurrency as wel ass add tags.
Next, we can set one or multiple sources.

![](2022-04-21-08-54-23.png)

Then we can choose whether to use a AWS managed docker image for the CodeBuild or we can create our own.

![](2022-04-21-08-55-19.png)

We can configure timeouts, certificates, VPC, compute scale, environment variables, file systems.

![](2022-04-21-08-56-08.png)

Choose how to define the build commands.

![](2022-04-21-08-56-27.png)

Allow batching

![](2022-04-21-08-56-46.png)

Define artifacts

![](2022-04-21-08-57-05.png)

Configure logging

![](2022-04-21-08-57-22.png)

---

Once created, if the buildspec.yml isn't in the root directory, it should fail.

![](2022-04-21-08-57-56.png)