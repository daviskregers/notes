# Testing the REST API

When deployed we got the list of our endpoints as outputs:

```console
endpoints:
  POST - https://wj34feq9gl.execute-api.eu-west-1.amazonaws.com/dev/todos
  GET - https://wj34feq9gl.execute-api.eu-west-1.amazonaws.com/dev/todos
  GET - https://wj34feq9gl.execute-api.eu-west-1.amazonaws.com/dev/todos/{id}
  PUT - https://wj34feq9gl.execute-api.eu-west-1.amazonaws.com/dev/todos/{id}
  DELETE - https://wj34feq9gl.execute-api.eu-west-1.amazonaws.com/dev/todos/{id}
```

We can use cUrl to test them:

```console

➜  06-aws-node-rest-api-with-dynamodb git:(master) ✗ curl --location --request POST 'https://wj34feq9gl.execute-api.eu-west-1.amazonaws.com/dev/todos' \
--header 'Content-Type: application/json' \
--data-raw '{"text":"Do something!"}'
{"id":"6a86c070-2b65-11ec-8afa-cb984a671a49","text":"Do something!","checked":false,"createdAt":1634047512055,"updatedAt":1634047512055}%                                                                                                 

➜  06-aws-node-rest-api-with-dynamodb git:(master) ✗ curl --location --request POST 'https://wj34feq9gl.execute-api.eu-west-1.amazonaws.com/dev/todos' \
--header 'Content-Type: application/json' \
--data-raw '{"text":"Do something else!"}'
{"id":"86ae3da0-2b65-11ec-8afa-cb984a671a49","text":"Do something else!","checked":false,"createdAt":1634047559290,"updatedAt":1634047559290}%                                                                                            

➜  06-aws-node-rest-api-with-dynamodb git:(master) ✗ curl --location --request GET 'https://wj34feq9gl.execute-api.eu-west-1.amazonaws.com/dev/todos'
[{"checked":false,"createdAt":1634047559290,"text":"Do something else!","id":"86ae3da0-2b65-11ec-8afa-cb984a671a49","updatedAt":1634047559290},{"checked":false,"createdAt":1634047512055,"text":"Do something!","id":"6a86c070-2b65-11ec-8afa-cb984a671a49","updatedAt":1634047512055}]%                                                                      

➜  06-aws-node-rest-api-with-dynamodb git:(master) ✗ curl --location --request GET 'https://wj34feq9gl.execute-api.eu-west-1.amazonaws.com/dev/todos/86ae3da0-2b65-11ec-8afa-cb984a671a49'
{"checked":false,"createdAt":1634047559290,"text":"Do something else!","id":"86ae3da0-2b65-11ec-8afa-cb984a671a49","updatedAt":1634047559290}%                                                                                            

➜  06-aws-node-rest-api-with-dynamodb git:(master) ✗ curl --location --request DELETE 'https://wj34feq9gl.execute-api.eu-west-1.amazonaws.com/dev/todos/86ae3da0-2b65-11ec-8afa-cb984a671a49'
{}%                                                                                                                  

➜  06-aws-node-rest-api-with-dynamodb git:(master) ✗ curl --location --request GET 'https://wj34feq9gl.execute-api.eu-west-1.amazonaws.com/dev/todos/86ae3da0-2b65-11ec-8afa-cb984a671a49'                                             

➜  06-aws-node-rest-api-with-dynamodb git:(master) ✗ curl --location --request GET 'https://wj34feq9gl.execute-api.eu-west-1.amazonaws.com/dev/todos'                                        
[{"checked":false,"createdAt":1634047512055,"text":"Do something!","id":"6a86c070-2b65-11ec-8afa-cb984a671a49","updatedAt":1634047512055}]%                                                                                               

➜  06-aws-node-rest-api-with-dynamodb git:(master) ✗ 
```

We can also see the items in our DynamoDB table.

![](2021-10-12-17-09-07.png)