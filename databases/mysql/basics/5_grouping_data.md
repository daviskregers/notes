# Grouping data

## GROUP BY

the `GROUP BY` clause groups a set of rows into a set of summary rows by values of columns or expressions. It returns one row for each group.

```sql
SELECT 
    c1, c2,..., cn, aggregate_function(ci)
FROM
    table
WHERE
    where_conditions
GROUP BY c1 , c2,...,cn;
```

The `GROUP BY` clause must appear after `FROM` and `WHERE` clauses. 

```sql
SELECT 
    status, COUNT(*)
FROM
    orders
GROUP BY status;
```

It also allows to sort the groups:

```sql
SELECT 
    status, COUNT(*)
FROM
    orders
GROUP BY status DESC;
```

## HAVING

The `HAVING` clause is often used with the `GROUP BY` to filter groups based on a specific condition. If it' s ommited, `HAVING` behaves like `WHERE`.

```sql
SELECT 
    ordernumber,
    SUM(quantityOrdered) AS itemsCount,
    SUM(priceeach*quantityOrdered) AS total
FROM
    orderdetails
GROUP BY ordernumber
HAVING total > 1000;
```

## ROLLUP

A grouping set is a set of columns to which you want to group. The `ROLLUP` clause is an extension of the `GROUP BY` clause with the following syntax:

```sql
SELECT 
    select_list
FROM 
    table_name
GROUP BY
    c1, c2, c3 WITH ROLLUP;
```

The `ROLLUP` generates multiple grouping sets based on the columns or expression specified in the `GROUP BY` clause.

## `GROUPING` function

To check whether `NULL` in the results set represents the subtotals or grand totals, you can use `GROUPING()` function. The `GROUPING` function will return 1 when NULL occurs in a supper-aggregate row, otherwise it will return 0.

```sql
SELECT 
    IF(GROUPING(orderYear),
        'All Years',
        orderYear) orderYear,
    IF(GROUPING(productLine),
        'All Product Lines',
        productLine) productLine,
    SUM(orderValue) totalOrderValue
FROM
    sales
GROUP BY 
    orderYear , 
    productline 
WITH ROLLUP;
```
