# Listing Stored procedures in database

MySQL provides us with several useful statements that help manage stored procedures more effectively. Those statements include listing stored procedures and showing the stored procedure's source code.

## Displaying characteristics of stored procedures

```sql
SHOW PROCEDURE STATUS [LIKE 'pattern' | WHERE expr]
```

You can use `LIKE` or `WHERE` clause to filter out stored procedures based on various criteria.

```sql
SHOW PROCEDURE STATUS WHERE db = 'classicmodels';
SHOW PROCEDURE STATUS WHERE name LIKE '%product%'
```

## Displaying stored procedure's source code

```sql
SHOW CREATE PROCEDURE stored_procedure_name
```