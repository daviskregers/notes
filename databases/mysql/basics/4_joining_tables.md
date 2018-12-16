# Jointing tables

## Aliases

Mysql supports 2 kinds of aliases - column aliases and table aliases.

```sql
SELECT 
 [column_1 | expression] AS descriptive_name
FROM table_name;
```

The `AS` is optional.

```sql
SELECT
 CONCAT_WS(', ', lastName, firstname) `Full name`
FROM
 employees
ORDER BY
 `Full name`;
```

```sql
SELECT
 customerName,
 COUNT(o.orderNumber) total
FROM
 customers c
INNER JOIN orders o ON c.customerNumber = o.customerNumber
GROUP BY
 customerName
ORDER BY
 total DESC;
```

## Join

The relational database consists of multiple related tables linking together using common columns called as `foreign key` columns.
A MySQL JOIN is a method of linking data between one (self-join) or more tables based on values of the common column between tables.

MySQL supports the following types of joins:

- Cross join
- Inner join
- Left join
- Right join

## Cross join

The `CROSS JOIN` makes a cartesian product of rows from multiple tables. When joining tables `t1` and `t2`, it will include combinations of rows from the `t1` table with the `t2` table.

```sql
SELECT 
    t1.id, t2.id
FROM
    t1
CROSS JOIN t2;
```

## Inner join

To form an `INNER JOIN`, there is a join-predicate needed that esentialy is a condition on which the columns get combined. The `INNER JOIN` requires rows in the two joined tables to have matching column values.
To join two tables, the `INNER JOIN` compares each row in the first table with each row in the second table to faind pairs of rows that satisfy the join-predicate. Whenever the join-predicate is satisfied by matching non-NULL values, column values for each matched pair of rows of the two tables are included in the result set.

```sql
SELECT 
    t1.id, t2.id
FROM
    t1
        INNER JOIN
    t2 ON t1.pattern = t2.pattern;
```

This means that rows in t1 and t2 must have the same values in the pattern column to be included in the result.

## Left join

Left join also requires a join predicate. Unlike the inner join, the left join returns all rows in the left table including rows that satisfy join-predicate and rows that do not.
For the rows that do not match the join predicate, NULL values appear in the column of the right table dataset.

```sql
SELECT 
    t1.id, t2.id
FROM
    t1
        LEFT JOIN
    t2 ON t1.pattern = t2.pattern
ORDER BY t1.id;
```

## Right join

The Righ join is similar to left join except that it' s reversed - every row of the right side table will appear and the left one will contain NULLs if the join-predicate is not satisfied.