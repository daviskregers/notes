# Deleting data in DynamoDB from lambda

We are going to set everything up like the previous sections and set up code for the `cy-delete-data` like so:

```js
const AWS = require('aws-sdk');
const dynamodb = new AWS.DynamoDB({
    region: 'eu-central-1',
    apiVersion: '2012-08-10'
});

exports.fn = (event, context, callback) => {
    
    const params = {
        Key: {
            "UserId": {
                S: "user_0.06768033925361383"
            }
        },
        TableName: 'compare-myself'
    }
    
    dynamodb.deleteItem(params, function(err, data) {
        if (err) {
            console.log(err);
            callback(err);
        } else {
            console.log(data);
            callback(null, data)
        }
    })
    
}
```