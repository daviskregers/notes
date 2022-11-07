# MySQL Subquery

A MySQL subquery is a query that is nested within another query. It can be nested into another subquery as well.

```sql
SELECT 
    lastName, firstName
FROM
    employees
WHERE
    officeCode IN (SELECT 
            officeCode
        FROM
            offices
        WHERE
            country = 'USA');
```

The subqueries can located in `WHERE` clauses, `IN`, `EXISTS`,  operators, `FROM` clauses.