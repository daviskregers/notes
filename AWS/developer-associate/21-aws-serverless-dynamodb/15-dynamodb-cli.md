# DynamoDB - Good to Know

- --projection-expression: one or more attributes to retrieve
- --filter-expression: filter items before returned to you

- General AWS CLI Pagination Options (e.g. DynamoDB, S3...)
    - --page-size: specify AWS CLI retrieves the full list of items but with larger number of API calls instead of one API call (default: 1000 items)
    - --max-items: max. number of items to show in the CLI (returns NextToken)
    - --starting-token: specify the last Nexttoken to retrieve the next set ot items

```console
# Projection Expression

$ aws dynamodb scan --table-name UserPosts --projection-expression "user_id, content"

# Filter Expression

$ aws dynamodb scan --table-name UserPosts --filter-expression "user_id = :u" --expression-attribute-values '{":u": {"S": "john123"}}'

# Page Size - will do 1 API call if you have 3 items

$ aws dynamodb scan --tablename UserPosts

# Will do 3 API calls if you have 3 Items

$ aws dynamodb scan --table-name UserPosts --page-size 1

# Max Items

$ aws dynamodb scan --table-name UserPosts --max-items 1

# Fetch the next item

$ aws dynamodb scan --table-name UserPosts --max-items 1 --starting-token eyJFeGN..
```