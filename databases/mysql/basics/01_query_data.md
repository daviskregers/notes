# Query data

## SELECT

The SELECT statement allows to get data from tables or views. It controls which columns and rows you want to see. 

```sql
SELECT 
    column_1, column_2, ...
FROM
    table_1
[INNER | LEFT |RIGHT] JOIN table_2 ON conditions
WHERE
    conditions
GROUP BY column_1
HAVING group_conditions
ORDER BY column_1
LIMIT offset, length;
```

## SELECT DISTINCT

When querying, it is possible to get duplicate rows. In order to remove duplicates, you can use `DISTINCT`.

```sql
SELECT DISTINCT
    columns
FROM
    table_name
WHERE
    where_conditions;
```

If a column has `NULL` value in the column, it will keep only the first occurence. When using multiple columns, it will look for unique combinations between the columns.

## DISTINCT vs GROUP BY

If you use GROUP BY without any aggregation functions, it behaves like DISTINCT.

```sql

SELECT 
    state
FROM
    customers
GROUP BY state;

```

is equal to

```sql

SELECT DISTINCT
    state
FROM
    customers;

```

## DISTINCT and aggregate function

You can also use DISTINCT in aggregate functions like this:

```sql

SELECT 
    COUNT(DISTINCT state)
FROM
    customers
WHERE
    country = 'USA';

```