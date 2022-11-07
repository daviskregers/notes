# Modifying data

## INSERT

The `INSERT` statement allows you to insert one or more rows into a table. The following illustrates the syntax:

```sql
INSERT INTO table(c1,c2,...)
VALUES (v1,v2,...);
```

First, you specify the table nme and list of comma-seperated columns inside parentheses. Then, you put a comma-separated lists of values of the corresponding columns inside.

```sql
INSERT INTO table(c1,c2,...)
VALUES 
   (v11,v12,...),
   (v21,v22,...),
    ...
   (vnn,vn2,...);
```

## INSERT INTO SELECT

Besides using row values in the `VALUES` clause, you can use the result of a `SELECT` statement as the data source for the INSERT statement.

```sql
INSERT INTO table_name(column_list)
SELECT 
   select_list 
FROM 
   another_table;
```

## INSERT IGNORE

When you use `INSERT` statement to add multiple rows to a table and if an error occurs during the processing, MySQL termintates the statement and returns an error. As the result, no rows are inserted into the table.

However, if you use `INSERT IGNORE` statement, the rows with invalid date that cause the error are ignored and the rows with valid data are inserted into the table.

```sql
INSERT IGNORE INTO table(column_list)
VALUES( value_list),
      ( value_list),
      ...
```

## UPDATE

We use `UPDATE` statement to update existing data in a table. We can use the `UPDATE` statement to change column values of a single row, group of rows or all rows in a table.

```sql
UPDATE [LOW_PRIORITY] [IGNORE] table_name 
SET 
    column_name1 = expr1,
    column_name2 = expr2,
    ...
WHERE
    condition;
```

Note when not providing `WHERE` statemtnt, it will update all the rows in the table.

MySQL supports two modifiers to the `UPDATE` statement. 

1. The `LOW_PRIORITY` modifier instructs the `UPDATE` statement to delay the update until there is no connection reading data from the table. The `LOW_PRIORITY` takes effect for the storage engines that use table-level locking only.

2. The `IGNORE` modifier enables the `UPDATE` statement to continue updating rows even if errors occured.

```sql
UPDATE employees 
SET 
    email = 'mary.patterson@classicmodelcars.com'
WHERE
    employeeNumber = 1056;
```

```sql
UPDATE customers 
SET 
    salesRepEmployeeNumber = (SELECT 
            employeeNumber
        FROM
            employees
        WHERE
            jobtitle = 'Sales Rep'
        LIMIT 1)
WHERE
    salesRepEmployeeNumber IS NULL;
```

## UPDATE JOIN

We often use join clauses to query rows in a table that have or may not have corresponding rows in another table. In MySQL we can use the JOIN clauses in the UPDATE statement to perform cross-table update.

```sql
UPDATE T1, T2,
[INNER JOIN | LEFT JOIN] T1 ON T1.C1 = T2. C1
SET T1.C2 = T2.C2, 
    T2.C3 = expr
WHERE condition
```

```sql
UPDATE T1,T2
INNER JOIN T2 ON T1.C1 = T2.C1
SET T1.C2 = T2.C2,
      T2.C3 = expr
WHERE condition
```

## DELETE

To delete data from a table you can use the `DELETE` statement. 

```sql
DELETE FROM table_name
WHERE condition;
```

1. You must specify the table you want to delete data from.
2. Use a condition to select which records you want to delete. The `WHERE` clause is optional, but with out it - it will delete every single record in the table.

```sql
DELETE FROM employees 
WHERE
    officeCode = 4;
```

```sql
DELETE FROM customers
WHERE country = 'France'
ORDER BY creditLimit
LIMIT 5;
```

## ON DELETE CASCADE

The `ON DELETE CASCADE` is used to delete referential data from child tables automatically when you delete the data from parent table.

```sql
CREATE TABLE buildings (
    building_no INT PRIMARY KEY AUTO_INCREMENT,
    building_name VARCHAR(255) NOT NULL,
    address VARCHAR(255) NOT NULL
);

CREATE TABLE rooms (
    room_no INT PRIMARY KEY AUTO_INCREMENT,
    room_name VARCHAR(255) NOT NULL,
    building_no INT NOT NULL,
    FOREIGN KEY (building_no)
        REFERENCES buildings (building_no)
        ON DELETE CASCADE
);
```

Whenever the building gets deleted that room is referenced to. The room will be deleted too.

### Finding tables affected by MySQL `ON DELETE CASCADE` action

```sql
USE information_schema;
 
SELECT 
    table_name
FROM
    referential_constraints
WHERE
    constraint_schema = 'classicmodels'
        AND referenced_table_name = 'buildings'
        AND delete_rule = 'CASCADE'
```

## DELETE JOIN

MySQL also allows you to use `JOIN` clause in the `DELETE` statement to delete rows from a table and the matching rows in another table.

```sql
DELETE T1, T2
FROM T1
INNER JOIN T2 ON T1.key = T2.key
WHERE condition;
```

```sql
DELETE t1,t2 FROM t1
        INNER JOIN
    t2 ON t2.ref = t1.id 
WHERE
    t1.id = 1;
```

```sql
DELETE T1 
FROM T1
        LEFT JOIN
    T2 ON T1.key = T2.key 
WHERE
    T2.key IS NULL;
```

## REPLACE

The `>REPLACE` statement is a MySQL extension to the standard SQL. The MySQL `REPLACE` statement works as follows:

- If the new row already does not exist, the `REPLACEMENT` statement inserts a new row.
If the new row already exist, the `REPLACE` statement deletes the old row and then inserts a new row.

To determine whether the new row already exists in the table, MySQL uses `PRIMARY KEY` or `UNIQUE KEY` index. If the table does not have one of these indexes, the `REPLACE` statement is equivalent to insert statement.

```sql
REPLACE INTO cities(name)
VALUES('Houston');
```

```sql
REPLACE INTO cities
SET id = 4,
    name = 'Phoenix',
    population = 1768980;
```

```sql
REPLACE INTO cities(name,population)
SELECT name,population FROM cities 
WHERE id = 1;
```

## Prepared statement

Prior MySQL version 4.1, the query is sent to the MySQL server in the textual format. In turn, MySQL returns the data to the client using textual protocol. MySQL has to fully parse the query and transform the result set into a string before returning it to the client.

The textual protocol has serious performance implication. To resolve this problem, MySQL added a new feature called prepared statements.

```sql
SELECT * 
FROM products 
WHERE productCode = ?;
```

### Usage

In order to use MySQL prepared statement, you need to use other three MySQL statements as follows:

1. `PREPARE` - prepares statement for execution
2. `EXECUTE` - Executes a prepared statement preparing by a PREPARE statement.
3. `DEALLOCATE PREPARE` - Releases prepared statement.

```sql
PREPARE stmt1 FROM 'SELECT productCode, productName
                    FROM products
                    WHERE productCode = ?';
 
SET @pc = 'S10_1678';
EXECUTE stmt1 USING @pc;
 
DEALLOCATE PREPARE stmt1;
```
