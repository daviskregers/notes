# Sorting data

When using `SELECT` statement, it is possible to use `ORDER BY` to order the results:

- single column or multiple column
- in ascending or descending order

```sql
SELECT column1, column2,...
FROM tbl
ORDER BY column1 [ASC|DESC], column2 [ASC|DESC],...
```

## Custom sort order

The `ORDER BY` clause enables you to define own custom sort order for the values in a column using `FIELD` function.

```sql
SELECT 
    orderNumber, status
FROM
    orders
ORDER BY FIELD(status,
        'In Process',
        'On Hold',
        'Cancelled',
        'Resolved',
        'Disputed',
        'Shipped');
```
