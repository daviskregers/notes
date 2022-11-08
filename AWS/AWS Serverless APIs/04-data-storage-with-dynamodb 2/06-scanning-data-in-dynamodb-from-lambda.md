# Scanning data in DynamoDB from lambda

We can do the same IAM steps from the last section and configure the `ct-get-data` lambda function:

```js
const AWS = require('aws-sdk');
const dynamodb = new AWS.DynamoDB({
    region: 'eu-central-1',
    apiVersion: '2012-08-10'
});

exports.fn = (event, context, callback) => {
    
    const type = event.type;
    
    if (type === 'all') {
        
        const params = {
            TableName: 'compare-myself'
        }
        
        dynamodb.scan(params, function(err, data) {
            if (err) {
                console.log(err)
                callback(err)
            } else {
                console.log(data)
                const items = data.Items.map((dataField) => {
                    return {
                        age: +dataField.Age.N,
                        height: +dataField.Height.N,
                        income: +dataField.Income.N
                    }
                });
                callback(null, items)
            }
        })
        
        callback(null, '')
    } else if (type === 'single') {
        
        const params = {
            Key: {
                "UserId": {
                    S: "user_0.06768033925361383"
                }
            },
            TableName: 'compare-myself'
        }
        
        dynamodb.getItem(params, function(err, data) {
            if (err) {
                console.log(err);
                callback(err);
            } else {
                console.log(data);
                callback(null, [{
                    age: +data.Age.N,
                    height: +data.Height.N,
                    income: +data.Income.N
                }])
            }
        })
        
        
    }  else {
        callback('Something went wrong!')    
    }
    
}
```