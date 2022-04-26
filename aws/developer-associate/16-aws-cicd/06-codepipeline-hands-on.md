# CodePipeline Hands On

We are going to create a new CodePipeline

![](img/2022-04-21-08-25-16.png)

![](img/2022-04-21-08-25-42.png)

![](img/2022-04-21-08-27-02.png)

Then selecting the change detection options the AWS CodePipeline option isn't really recommended as it will periodically check for changes and it can take time until it's picked up.

![](img/2022-04-21-08-28-04.png)

![](img/2022-04-21-08-28-42.png)

![](img/2022-04-21-08-30-19.png)

When the pipeline is created you can create your own stages and in them you can have multiple action groups.

![](img/2022-04-21-08-34-02.png)

The actions in an action group will be done in parallel, the next action group will be sequential.