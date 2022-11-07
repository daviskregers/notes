# Filter data

## MySQL WHERE

Where clause allows to specify the search condition.

```sql

SELECT 
    select_list
FROM
    table_name
WHERE
    search_condition;

```

search combination of one or more predicates that are combined with `AND`, `OR`, `NOT` operators. In SQL predicate is an expression that evaluates to true, false or unknown.
Any row that causes the search condition to be true, will be included in the result set.

Where statement can be used not only in select, but in update and delete statements as well.

```sql

SELECT * FROM table_name
WHERE (a > 0 AND b < 5 AND c IS NULL) OR d > 100

```

Some of the most popular logical operators in where statements are as follows:

- AND       - all expressions must be true

```sql
SELECT 
    customername, 
    country, 
    state
FROM
    customers
WHERE
    country = 'USA' AND state = 'CA';
```

- OR        - one of expressions must be true

```sql
SELECT 
    customername, 
    country, 
    state
FROM
    customers
WHERE
    country = 'USA' OR country = 'Canada';
```

- IN        - determine if the column value is in a list of values
```sql
SELECT 
    customername, 
    country, 
    state
FROM
    customers
WHERE
    country IN ('USA' , 'Canada')
```

Basicaly a shorter OR statement. Can be also used with subqueries.

```sql
SELECT 
    orderNumber, 
    customerNumber, 
    status, 
    shippedDate
FROM
    orders
WHERE
    orderNumber IN (SELECT 
            orderNumber
        FROM
            orderDetails
        GROUP BY orderNumber
        HAVING SUM(quantityOrdered * priceEach) > 60000);
```

- BETWEEN   - value must be in a given range

```sql
SELECT 
    customername, 
    country, 
    state
FROM
    customers
WHERE
    country = 'USA' AND state = 'CA';
```

- LIKE      - must follow a specific pattern. 

Provides two operators `%` and `_`. Where `%` is a string of zero or more characters. `_` matches any single character.

```sql
SELECT 
    employeeNumber, 
    lastName, 
    firstName
FROM
    employees
WHERE
    lastname LIKE '%on%';
```

```sql
SELECT 
    employeeNumber, 
    lastName, 
    firstName
FROM
    employees
WHERE
    firstname LIKE 'T_m';
```

In order to match the `_` symbol, you need to escape it:

```sql
SELECT 
    productCode, 
    productName
FROM
    products
WHERE
    productCode LIKE '%\_20%';
```

- IS NULL   - the value is null

```sql

SELECT 
    customerName, 
    country, 
    salesrepemployeenumber
FROM
    customers
WHERE
    salesRepEmployeeNumber = 1370 OR
    salesRepEmployeeNumber IS NULL;

```