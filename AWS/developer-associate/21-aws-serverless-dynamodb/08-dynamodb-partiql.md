# DynamoDB - PartiQL

- Use an SQL-likey syntax to manipulate DynamoDB tables

```sql
SELECT *
FROM "demo_indexes"
WHERE "user_id" = "partitionKeyValue" AND "game_ts" = "sortKeyValue"
```

- Supports some (but not all) statements:
    - INSERT
    - UPDATE
    - SELECT
    - DELETE
- It supports Batch operations

The editor can be acessed in the left sidebar.

![](2022-05-17-07-50-14.png)

