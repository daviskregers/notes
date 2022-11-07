# Building the REST API

The code is from https://github.com/serverless/examples

We are going to download that repository and do the following things:

```console
➜  06-aws-node-rest-api-with-dynamodb git:(master) ✗ npm i
npm WARN deprecated uuid@2.0.3: Please upgrade  to version 7 or higher.  Older versions may use Math.random() in certain circumstances, which is known to be problematic.  See https://v8.dev/blog/math-random for details.

added 1 package, and audited 2 packages in 610ms

found 0 vulnerabilities
```

We can examine the serverless.yml file and see that there are some interesting things there, like:

```yaml
    DYNAMODB_TABLE: ${self:service}-${opt:stage, self:provider.stage}
```

The table name will be the same as the service name defined at the root, with a suffix of it's stage.

The stage comes from option that are specified either when deploying sls or it will use the provider stage which is `dev` by default.

---

Also, the IAM roles are specifying only the permissions we need on one specific table.

```yaml
  iamRoleStatements:
    - Effect: Allow
      Action:
        - dynamodb:Query
        - dynamodb:Scan
        - dynamodb:GetItem
        - dynamodb:PutItem
        - dynamodb:UpdateItem
        - dynamodb:DeleteItem
      Resource: "arn:aws:dynamodb:${opt:region, self:provider.region}:*:table/${self:provider.environment.DYNAMODB_TABLE}"
```

---

The functions are defined like this:

```yaml
  get:
    handler: todos/get.get
    events:
      - http:
          path: todos/{id}
          method: get
          cors: true
```

The handler in this case is located at the `todos/get.js`, it has a method `get`.

The event is coming from API Gateway, with a path of `todo/{id}`, method `GET`.

The CORS variable specifies if the endpoint can be called from other domains.

---

Finally, at the end of the file we can see the Resources which basically is a CloudFormation template.

```yaml
resources:
  Resources:
    TodosDynamoDbTable:
      Type: 'AWS::DynamoDB::Table'
      DeletionPolicy: Retain
      Properties:
        AttributeDefinitions:
          -
            AttributeName: id
            AttributeType: S
        KeySchema:
          -
            AttributeName: id
            KeyType: HASH
        ProvisionedThroughput:
          ReadCapacityUnits: 1
          WriteCapacityUnits: 1
        TableName: ${self:provider.environment.DYNAMODB_TABLE}
```

It lists resources we need to create. In this case we create a `TodosDynamoDbTable` table.