# Using set operators

## MySQL UNION operator

MySQL UNION operator allows you to combine two or more result sets of queries into a single result set.

```sql
SELECT column_list
UNION [DISTINCT | ALL]
SELECT column_list
UNION [DISTINCT | ALL]
SELECT column_list
...
```

To combine result set of two or more queries using the UNION operator, there are the basic rules that you must follow:

- First, the number and the orders of columns that appear in all SELECT statements must be the same;
- Second, the data types of columns must be the same or convertible.

By default, the UNION operator removes duplicate rows even if you don't specify the DISTINCT operator explicity.

If you use `UNION ALL` explicitly, the duplicate rows, if available, remain in the results. Because `UNION ALL` does not need to handle duplicates, it performs faster than `UNION DISTINCT`.

## INTERSECT

The `INTERSECT` operator is a set operator that returns only distinct rows of two queries or more.

```sql
(SELECT column_list 
FROM table_1)
INTERSECT
(SELECT column_list
FROM table_2);
```

Same as the UNION, it has to have the same order and number of columns. The data types must be compatible.

## MINUS

`MINUS` compares results of two queries and returns distinct rows from the first query that aren' t output by the second query.

```sql
SELECT column_list_1 FROM table_1
MINUS 
SELECT columns_list_2 FROM table_2;
```

Same as the UNION, it has to have the same order and number of columns. The data types must be compatible.