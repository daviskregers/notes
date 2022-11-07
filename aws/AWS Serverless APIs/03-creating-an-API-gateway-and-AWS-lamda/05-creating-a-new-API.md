# Creating a new API

We are going to create a new API with a resource `compare-yourself` and 3 methods - `POST`, `GET` and `DELETE`.

![](../../../images/2019-10-05-09-18-06.png)

# Creating an API

When creating a new API we have multiple options on how to go about this:
- We can create either a REST or WebSockets API. 
- We can create a new API, import an existing one, import it from a text file in swagger/open api format, create an preset example API.

You can click on the `example API` to see on how the swagger format looks like.

![](../../../images/2019-10-05-10-03-50.png)

# Creating resources

Now we have to create the `compare-yourself` resource, we can do that under `Action -> Create resource`. Note that the resources are hierarchical and we need to make sure we have selected the right resource before we are doing this. Currently we have only root resource, so we are ok.

![](../../../images/2019-10-05-10-07-15.png)

You can define the resource name and path which can be different.

![](../../../images/2019-10-05-10-07-55.png)

The `configure as proxy resource` option means that this will be a catch-all resource that catches all methods and paths under it and pass it to other services.

The CORS option is a security option. This option will allow you to access the API from a different server as well introduce `OPTIONS` endpoint that is sent to check endpoint availablility.

![](../../../images/2019-10-05-10-15-48.png)
![](../../../images/2019-10-05-10-16-07.png)
![](../../../images/2019-10-05-10-17-14.png)

# Creating an HTTP method

Now, while making sure we have selected the `compare-yourself` reource, we can click on `Actions -> Create Method`.

![](../../../images/2019-10-05-10-19-35.png)

Then you can choose the method type, we want to select `POST`.
Then it will bring up setup wizard, where we can choose what integration type it has:

- Lambda function - run some code on demand
- HTTP - we can pass trough to another HTTP service
- Mock - return a dummy response
- AWS service - pass trough to another AWS service

We want to select the `lambda function`.

The option `Use lambda proxy` will take the incoming requests and it's headers, pass that as json object to the lambda function. You will need to extract what you need and return a response. 

![](../../../../images/2019-10-05-10-28-50.png)

## Creating a lambda function

Let's click on the `Create a lambda Function` link, which will bring us to the lambda console.

![](../../../images/2019-10-05-10-31-22.png)

Once we click on `Create Function` it will open up the lambda function.

![](../../../images/2019-10-05-10-32-27.png)

The designer section will list all the triggers that calls the function as well all the access permissions it has. By default it has no triggers and has access to write on cloudwatch logs.

In the monitoring section we can see statistics, logs about the function.

On the bottom you can see the function code, which is the code that is being run when executing the function.

We can also set environment variables, tags as well as other settings on this page.

## Connecting lamda functions to API Gateway

When we have created a lamda function, we are going to change the lambda region to other one and back to refresh the list, start writing the lamda function name, select the correct one.
![](../../../images/2019-10-05-10-40-30.png)

Now we can click on the test button which is over the `client`.

![](../../../images/2019-10-05-10-41-49.png)

This will open up a page where we can test the endpoint.

![](../../../images/2019-10-05-10-42-27.png)

## Accessing the API from the WEB & Fixing CORS issues

In order to access the API from the web, we need to deploy it, we can check this in the stages section.

![](../../../images/2019-10-05-10-44-44.png)

So, we are going to call `Actions -> Deploy API`.

![](../../../images/2019-10-05-10-45-20.png)

![](../../../images/2019-10-05-10-46-03.png)

And this is going to create a new stage that gives us an URL, configuration for the stage

![](../../../images/2019-10-05-10-47-06.png)

Now, if we would request the POST method from our website, it would return a CORS error:

![](../../../images/2019-10-05-10-49-13.png)

To fix this, we are going to `resurces -> post method -> method response` and under `Response headers for 200` add `Access-Control-Allow-Origin`.

![](../../../images/2019-10-05-10-51-38.png)

And then under `Integration Response`, we can provide it's value. It will be a wildcard in this case.

![](../../../images/2019-10-05-10-52-57.png)

## Body Mapping templates

Under `Integration Request` we can set `Body Mapping templates`.

![](../../../images/2019-10-05-11-09-25.png)

This will give us a configuration where we can configure on what data is sent to the lambda function as an event.

For reference on how to use the template we can look up [http://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-mapping-template-reference.html](http://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-mapping-template-reference.html)

We can customize with something like this.

```json
{
    "age" : $input.json('$.personData.age'),
}
```

The `$` refers to request body.

We can also use `Body mapping templates` in the `Integration Response` as well.

![](../../../images/2019-10-05-11-16-10.png)

## Using Models & Validating requests

We can go to the `Models` section and create a model.

![](../../../images/2019-10-05-11-19-24.png)

When created, we can go to `Method Request` and add the model.

![](../../../images/2019-10-05-11-20-47.png)

This will ensure validating all the data that is set in the model according to it's schema.

![](../../../images/2019-10-05-11-21-57.png)

The json schema can be referenced from here:
- [https://json-schema.org/](https://json-schema.org/)
- [https://json-schema.org/understanding-json-schema/index.html](https://json-schema.org/understanding-json-schema/index.html)

Also now, if we go back to `Body mapping templates`, we can set model templates:

![](../../../images/2019-10-05-11-25-36.png)

The template can be modified as well

![](../../../images/2019-10-05-11-27-24.png)

## Adding a DELETE method

We are going to do the same steps as previously for creating a DELETE method and creating lambda function for it.

## Using path parameters

We can create an new child resource with a variable `type`.

![](../../../images/2019-10-05-11-43-50.png)

Under that, we can create a get method with a lambda function assigned to it.

![](../../../images/2019-10-05-11-45-48.png)

And in the `Body mapping templates` we can put something like this:

![](../../../images/2019-10-05-11-50-11.png)

## Accessing the API from the Web the right way

When selecting a resource, we can go to `Actions -> Enable CORS` to setup CORS.

![](../../../images/2019-10-05-11-52-22.png)