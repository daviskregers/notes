# API-specific features and options

Previously we created a resource and it's method.

The resource defines a path in the url. 

One thing to note is that when we are working on these things, they aren't live. We need to deploy them under the actions. Only then we will able to see them on the web.

The actual work happends under resources section.

![](../../../images/2019-10-05-09-37-38.png)

Then under stages section we can we can get information about the deployment.

![](../../../images/2019-10-05-09-38-49.png)

Under the `Authorizers` section we can add authentication to our APi. For certain resources that needs certain authentication, we can manage it here.

![](../../../images/2019-10-05-09-41-00.png)

The `Models` section, we can define the shape of the data we are working on. It is provided in JSON format.

![](../../../images/2019-10-05-09-41-32.png)

In the `Documentation` section we can create documentation for the API so people can know on how to use it.

The `Binary support` section is used when we are sending files in the requests.

The `Dashboard` shows shows stats about the API.

![](../../../images/2019-10-05-09-43-49.png)

The `Resource Policy` section is used to control how the API is accessed. We can whitelist and/or blacklist resources.

![](../../../images/2019-10-05-09-44-44.png)