# Querying data - SELECT

One of the most common tasks, when you work with PostgreSQL, is to query data from tables using the `SELECT` statement. The `SELECT` is one of the most complex statements in PostgreSQL. It has many clauses that you can combine to form a powerful query.

Because of it's complexity, we divide the the PostgreSQL `SELECT` statement tutorial into many shorter tutorials so that you can learn each clause of the `SELECT` statement easier. The following are the clauses that appear in the `SELECT` statement:

- Select distinct rows by using `DISTINCT` operator.
- Filter rows by using `WHERE` clause
- Sort rows by using `ORDER BY` clause
- Select rows based on various operators such as `BETWEEN`, `IN`, `LIKE`.
- Group rows into groups using `GROUP BY`
- Apply conditions for groups using `HAVING`
- Join a table to other tables using `INNER JOIN`, `LEFT JOIN`, `FULL OUTER JOIN`, `CROSS JOIN`.

In this tutorial we are using the `SELECT` with `FROM` clause.

## PostgreSQL `SELECT` statement syntax

Let's start with a basic form of the `SELECT` statement that retrieves data from a single table.

```sql
SELECT
    column1,
    column2,
    ...
FROM
    table_name;
```