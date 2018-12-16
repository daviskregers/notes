# Common table expression or CTE

A common table expression is not stored as an object and last only during the execution of a query. Different from a derived table, a CTE can be self-referencing or can be referenced multiple times in the same query. In addition, a CTE provides better readability and performance in comparison of a derived table.

The structure of a CTE includes the name, an optional column list, and a query that defines it. After the CTE definition, you can use it lika view in `SELECT`, `INSERT`, `UPDATE`, `DELETE`, or `CREATE VIEW` statement.

```sql
WITH cte_name (column_list) AS (
    query
) 
SELECT * FROM cte_name;
```

The number of columns in the query must be the same as the number of columns in the column_list. 

```sql
WITH customers_in_usa AS (
    SELECT 
        customerName, state
    FROM
        customers
    WHERE
        country = 'USA'
) SELECT 
    customerName
 FROM
    customers_in_usa
 WHERE
    state = 'CA'
 ORDER BY customerName;
```

```sql
ITH salesrep AS (
    SELECT 
        employeeNumber,
        CONCAT(firstName, ' ', lastName) AS salesrepName
    FROM
        employees
    WHERE
        jobTitle = 'Sales Rep'
),
customer_salesrep AS (
    SELECT 
        customerName, salesrepName
    FROM
        customers
            INNER JOIN
        salesrep ON employeeNumber = salesrepEmployeeNumber
)
SELECT 
    *
FROM
    customer_salesrep
ORDER BY customerName;
```

## Recursive CTE

```sql

WITH RECURSIVE cte_name AS (
    initial_query  -- anchor member
    UNION ALL
    recursive_query -- recursive member that references to the CTE name
)
SELECT * FROM cte_name;
```

```sql
WITH RECURSIVE employee_paths AS
  ( SELECT employeeNumber,
           reportsTo managerNumber,
           officeCode, 
           1 lvl
   FROM employees
   WHERE reportsTo IS NULL
     UNION ALL
     SELECT e.employeeNumber,
            e.reportsTo,
            e.officeCode,
            lvl+1
     FROM employees e
     INNER JOIN employee_paths ep ON ep.employeeNumber = e.reportsTo )
SELECT employeeNumber,
       managerNumber,
       lvl,
       city
FROM employee_paths ep
INNER JOIN offices o USING (officeCode)
ORDER BY lvl, city;
```