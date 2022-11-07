# Retrieving users from custom authorizers

We can modify the API's POS mapping template to retrieve the user from custom authorizer.

```json
#set($inputRoot = $input.path('$'))
{
    "age" : "$inputRoot.age",
    "height" : "$inputRoot.height",
    "income" : "$inputRoot.income",
    "userId" : "$context.authorizer.principalId",
}
```

Then we can go back to the POST lambda file and change the hardcoded user id from:

```js
S: "user_" + Math.random()
```

to: 
```js
S: event.userId
```