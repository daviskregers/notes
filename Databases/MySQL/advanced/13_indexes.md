# MySQL indexes

MySQL uses indexes to quickly find rows with specific column values. Without an index, MySQL must scan the whole table to locate the relevant rows. The larger table, the slower it searches.

## Creating indexes

### The phone book analogy

Suppose you have a phone book that contains all the names and phone numbers of people in a city. Let's say you want to find Bob Cat's phone number. Knowing that the names are alphabetically ordered, you first look for the page where the last name is Cat, then you look for Bob and his phone number.

Now, if the names in the phone book were not sorted alphabetically, you would need to go through all pages, reading every name in it ultil you find Bob Cat. This is called sequential searching. You go over all the entries until you find the person with the phone number that you are looking for.

Relating the phone book to the database table, if you have a phonebook table and you have to find the phone number of Bob Cat, you  would perform the following query:

```sql
SELECT phone_number
FROM phone_book
WHERE first_name = 'Bob' AND last_name = 'Cat;
```

It is pretty easy. Although thje query is fast, the database has to scan all the rows of the table until it finds the row. If the table has millions of rows, without an index, the data retrieval would take a lot of time to return the result.

### Introduction to index

An index is a data structure such as B-Tree that improves the speed of data retrieval on a table at the cost of additional writes and storage to maintain it.

The query optimizer may use indexes to quickly locate data without having to scan every row in a table for a given query.

When you create a table with a primary key or unique key, MySQL automatically creates a special index named `PRIMARY`. This index is called the clustered index.

The `PRIMARY` index is special because the index itself is stored together with the data in the same table. The clustered index enforces the order of rows in the table.

Other indexes other than the `PRIMARY` index are called secindary indexes or non-clustered indexes.

### CREATE INDEX statement

Typically, you create indexes for a table at the time of creation. For example, the following statement creates a new table with an index that consists of two columns c2 and c3.

```sql
CREATE TABLE t(
   c1 INT PRIMARY KEY,
   c2 INT NOT NULL,
   c3 INT NOT NULL,
   c4 VARCHAR(10),
   INDEX (c2,c3) 
);
```

To add an index for a column or a set of columns you use `CREATE INDEX` statement as follows:

```sql
CREATE INDEX index_name ON table_name (column_list)
```

To create an index for a column or a list of columns, you specify the index name, the table to which the index belongs, and the column list.

For example, to add a new index for the column c54, you use the following statement:

```sql
CREATE INDEX idx_c4 ON t(c4);
```

By default, MySQL creates the B-Tree index if you don't specify the index type. The following shows the permissible index type based on the storage engine of the table.

<table>
    <tr>
    <th>Storage Engine</th>
    <th>Allowed Index Types</th>
    </tr>
    <tr>
        <td>InnoDB</td><td>BTREE</td>
    </tr>
    <tr>
        <td>MyISAM</td><td>BTREE</td>
    </tr>
    <tr>
        <td>MEMORY/HEAP</td>
        <td>HASH,&nbsp;BTREE</td>
    </tr>
</table>

### MySQL CREATE INDEX example

The following statement finds employees whose job title is `Sales Rep`:

```sql
SELECT employeeNumber, lastName, firstName
FROM employees
WHERE jobTitle = 'Sales Rep';
```

To see how MySQL internally performed this query, you add the `EXPLAIN` clause at the beginning of the `SELECT` statement as follows:

Now, let's create an index for the `jobTitle` column by using the `CREATE INDEX` statement:

```sql
CREATE INDEX jobTitle on employees(jobTitle);
```

To show the indexes of a table, you use the `SHOW IDNEXES` statement, for example

```sql
SHOW INDEXES FROM employees
```


## MySQL DROP INDEX

To remove an existing index from a table, you use `DROP INDEX` statement as follows:

```sql
DROP INDEX index_name ON table_name
[algorithm_option | lock_option]
```

### Algorithm

The `algorithm_option` allows you to specify a specific algorithm used for the index removal. The following shows the syntax of the `algorithm_option` clause:

```sql
ALGORITHM [=] {DEFAULT|INPLACE|COPY}
```

For the index removal, the following algorithms are supported:

- `COPY`: The table is copied to the new table row by row, the `DROP INDEX` is them performed on the copy of the original table. The concurrent data manipulation statements such as INSERT and UPDATE are not permitted.
- `INPLACE` the table is rebuild in place instead of copied to the new one. MySQL issues an exclussive metadata lock on the table during the preparation and execution phases of the index removal operation. This algorithm allows concurrent data manupulation statements.

Note that the `ALGORITHM` clause is optional. MySQL uses `INPLACE`. In case the `INPLACE` is not supported, MySQL uses `COPY`.

### Lock

The `lock_option` controls the level of concurrent reads and writes on the table while the indewx is being removed.

The following shows the syntax of the `lock_option`:

```sql
LOCK [=] {DEFAULT|NONE\SHARED|EXCLUSIVE}
```

The following locking modes are supported:

- `DEFAULT` - this allows you to have the maximum level of concurrency for a given algorithm. First, it allows concurrent reads and writes if supported. If not, allow concurrent reads if supported. If not, eforce exclussive access.
- `NONE` if the `NONE` is supported, you can have concurrent reads and writes. Otherwise, MySQL issues an error.
- `SHARED` - if the `SHARED` is supported, you can have concurrent reads, but not writes. MySQL issues an error if the concurrent reads are not supported.
- `EXCLUSIVE` - this enforces exclusive access.

### `DROP INDEX` examples

```sql
DROP INDEX name ON leads;
```

```sql
DROP INDEX email ON leads
ALGORITHM = INPLACE 
LOCK = DEFAULT;
```

```sql
DROP INDEX `PRIMARY` ON table_name;
```

```sql
DROP INDEX `PRIMARY` ON t;
```

## MySQL SHOW INDEXES

To query the index information of a table, you use the `SHOW INDEXES` statement as follows:

```sql
SHOW INDEXES FROM table_name
```

To get the index of a table, you specify the table name after the `FROM` keyword. The statement will return the index information associated with the table in the current database.

You can specify the database name if you are not connected to any database or you want to get the index information of a table in a different database:

```sql
SHOW INDEXES FROM table_name 
IN database_name;
```

```sql
SHOW INDEXES FROM database_name.table_name;
```

The `SHOW INDEXES` will return following information

- `table` - name of the table
- `non_unique` - 1 if the index can contain duplicates, 0 if it can.
- `key_name` - the name of the index. The primary key index always has the name of `PRIMARY`.
- `seq_in_index` - The column sequence number in the index. The first column sequence number starts from 1.
- `column_name` - the column name
- `collation` - collation represents how the column is sorted in the index. `A` means ascending, `B` means descending, `NULL` means not sorted.
- `cadinality` - the cardinality returns an estimated number of unique values in the index. Note that the higher the cardinality, the greater the chance that the query optimizer uses the index for lookups.
- `sub_part` - The index prefix. It is null if the entire column is indexed. Otherwise, it shows the number of indexed charasteristics in case column is partially indexed.
- `packed` - indicates how the key is packed; NUL if it is not.
- `null` - `YES` - if the column may contain NULL values and blank if it does not.
- `index_type` prepresents the index method used such as `BTREE`, `HASH`, `RTREE` or `FULLTEXT`.
- `comment` - the information about the index not described in its own column.
- `index_comment` - shows the comment for the index specified when you create index with the `COMMENT` attribute.
- `visible` - whether the index is visible or invisible to the query optimizer or not; `YES` if is, `NO` if not.
- `expression` - if the index uses an expression rather than column or column prefix value, the expression indicates the expression for the key part and also the `column_name` column is NULL.

To filter index information, you can use a `WHERE` clause as follows:

```sql
SHOW INDEXES FROM table_name
WHERE condition;
```

You can use any information returned by the `SHOW INDEXES` statement to filter the index information. For example, the following statement returns only the invisible indexes of a table:

```sql
SHOW INDEXES FROM table_name
WHERE VISIBLE = 'NO';
```

## Using MySQL UNIQUE Index to prevent duplicates

To enforce the uniqueness value of one or more columns, you often use the `PRIMARY KEY` constraint. However, each table can have only one primary key. Hence, if you want to have a more than one column or a set of columns with unique values, you cannot use the primary key constraint.

Luckily, MySQL provides another kind of index called `UNIQUE` index that allows you to enforce the uniqueness of values in one or more columns. Unlike the `PRIMARY KEY` index, you can have more that one `UNIQUE` index per table.

To create a `UNIQUE` index, you use the `CREATE UNIQUE INDEX` statement as follows:

```sql
CREATE UNIQUE INDEX index_name
ON table_name(index_column_1,index_column_2,...);
```

Another way to enforce the uniqueness of value in one or more columns is to use the `UNIQUE` constraing.

When you create a `UNIQUE constraint`, MySQL creates an `UNIQUE` index behind the scenes.

The following statement illustrates how to create a unique contraing when you create a table.

```sql
CREATE TABLE table_name(
...
   UNIQUE KEY(index_column_,index_column_2,...) 
);
```

In this statement you can also use the `UNIQUE INDEX` instead of `UNIQUE KEY` because they are synonyms.

If you want to add constraint to an existing table, you can use the `ALTER TABLE` statement as follows:

```sql
ALTER TABLE table_name
ADD CONSTRAINT constraint_name UNIQUE KEY(column_1,column_2,...);
```

### UNIQUE Index and NULL

Unlike other database systems, MySQL considers NULL values as distinct values. Therefore, you can have multiple NULL values in the UNIQUE index.

This is how MySQL was designed. It is not a bug even though it was reported as a bug.

Another important point is that the `UNIQUE` constraint does not apply to NULL values except for the BDB storage engine.

## Prefix index

When you create a secondary index for a column, MySQL stores the values of the columns in a separate data structure e.g., B-Tree and Hash. 

In case the columns are the string columns, the index will consume a lot of disk space and potentially slow down the `INSERT` operations.

To address this issue, MySQL allows you to create an index for the leading part of the column values of the string columns using the following syntax:

```sql
column_name(length)
```

For example, the following statement creates the column prefix key part at the time of table creation:

```sql
CREATE TABLE table_name(
    column_list,
    INDEX(column_name(length))
)
```

Or add an index to an existing table:

```sql
CREATE INDEX index_name
ON table_name(column_name(length))
```

In this syntax, the length is the number of characters for the non-binary string types such as `CHAR`, `VARCHAR`, and `TEXT` and the number of byters for binary string types e.g., `BINARY`, `VARBINARY` AND `BLOB`.

MySQL allows you to optionally create column prefix key parts for `CHAR`, `VARCHAR`, `BINARY` and `VARBINARY` columns. If you create indexes for `BLOB` and `TEXT` columns, you must specify the column prefix key parts.

Notice that the prefix support and lengths of prefixes it supported are storage engine dependent. For InnoDB tables with `REDUNDAT` or `COMPACT` row format, the  maximum prefix length is 767 bytes. However, for the InnoDB tables with the `DYNAMIC` or `COMPRESSED` row format, the prefix lkength is 3072 bytes. MyISAM tables have the prefix length up to 1000 bytes.

### Prefix index example

The following query finds the products whose names start with the string 1970:

```sql
SELECT  productName, buyPrice, msrp
FROM products
WHERE productName LIKE '1970%';
```

Because there is not index for the productName column, the query optimizer has to scan all rows to return the result as shown in the output of the `EXPLAIN` statement below:

```sql
EXPLAIN SELECT productName, buyPrice, msrp
FROM products
WHERE productName LIKE '1970%';
```

If you often find the products by the product name, then you should create an index for this column because if will be more efficient for searches.

The size of the product name column is 70 characters. We can use the column prefix key parts.

The next question is how do you choose the length of the prefix? For doing this you can investigate the existing data. The goal is to maximize the uniqueness of the values in the column when you use the prefix.

Yo do this you can follow these steps:

- 1. Find the number of rows in table:

```sql
SELECT COUNT(*)
FROM products;
```

- 2. Evaluate different prefix length until you can achgieve the reasonable uniqueness or rows:

```sql
SELECT COUNT(DISTINCT LEFT(productName, 20)) unique_rows
FROM products;
```

From the output, 20 is a good prefix length in this case because if we use the first 20 characters of the product name for the index, all product names are unique.

Let's create an index with the prefix length 20 for the productName column:

```sql
CREATE INDEX idx_productname
ON products(producName(20));
```

And execute the query that finds products whose name starts with the string 1970 again:

```sql
EXPLAIN SELECT productName, buyPrice, msrp
FROM products
WHERE productName LIKE '1970%';
```

Now the query optimizer uses the newly created index which is much faster and more efficient than before.

## Invisible index

The invisible indexes allow you to mark indexes as unavailable for the query optimizer. MySQL maintains the invisible indexes and keeps them up to date when the data in the columns associated with the indexes changes.

By default, indexes are visible. To make them invisible, you have to explicitly declare its visiblility at the time of creating, or by using the `ALTER TABLE` command. MySQL provides us with the `VISIBLE` and `INVISIBLE` keywords to maintain index visibility.

```sql
CREATE INDEX index_name
ON table_name( c1, c2, ...) INVISIBLE;
```

For example, the following statement creates an index on the `extension` column of the employees table in the sample database and marks it as an invisible index:

```sql
CREATE INDEX extension 
ON employees(extension) INVISIBLE;
```

To change the visibility of existing indexes, you use the following statement:

```sql
ALTER TABLE table_name
ALTER INDEX index_name [VISIBLE | INVISIBLE];
```

You can find the indexes and their visibility by querying the `statistics` table in the `information_schema` database:

```sql
SELECT 
    index_name, 
    is_visible
FROM
    information_schema.statistics
WHERE
    table_schema = 'classicmodels'
        AND table_name = 'employees';
```

In addition, you can use the `SHOW INDEXES` command to display all indexes of table:

```sql
SHOW INDEXES FROM employees;
```

As mentioned earlier, the query optimizer does not use invisible index so why do you use the invisible index in the first place? Practically speaking, invisible indexes have a number of applications. For example, you can make an index invisible to see if has an impact to the performance and mark the index visible again if it does.

### Invisible index and primary key

The index of the primary key column cannot be invisible. If you try to do so, it MySQL will issue an error. 

In addition, an implicit primary key index also cannot be invisible. When you define a `UNIQUE` index on a `NOT NULL` column of a table that does not have a primary key, MySQL implicitly understands that this column is the primary key column and does not allow you to make the index invisible.

Consider the following example.

### Invisible index system variables

To control indexes used by the query optimizer, MySQL uses the `use_invisible_indexes` flag of the `optimizer_switch` system variable. By default, the `use_invisible_indexes` is off:

```sql
SELECT @@optimizer_switch;
```

## Descending index

A descending index is an index that stores key values in a descending order. Before MySQL 8.0, you can specify the `DESC` in an index definition. However, MySQL ignored it. In the meantime, MySQL could scan the index in reverse order but it comes at a high cost.

Starting from MySQL 8.0, the key values are stored in the descending order if you use the `DESC` keyword in the index definition. The query optimizer can take advantage of descending index when descending order is requested in the query.

For example, we create `t` table with for indexes in different orders:

```sql
DROP TABLE t;
 
CREATE TABLE t (
    a INT,
    b INT,
    INDEX a_asc_b_asc (a ASC , b ASC),
    INDEX a_asc_b_desc (a ASC , b DESC),
    INDEX a_desc_b_asc (a DESC , b ASC),
    INDEX a_desc_b_desc (a DESC , b DESC)
);
```

Second, use the following the following stored procedure to insert rows into the `t` table:

```sql
CREATE PROCEDURE insertSampleData(
    IN rowCount INT, 
    IN low INT, 
    IN high INT
)
BEGIN
    DECLARE counter INT DEFAULT 0;
    REPEAT
        SET counter := counter + 1;
        -- insert data
        INSERT INTO t(a,b)
        VALUES(
            ROUND((RAND() * (high-low))+high),
            ROUND((RAND() * (high-low))+high)
        );
    UNTIL counter >= rowCount
    END REPEAT;
END$$    
```

The stored procedure inserts a number or rows with the values between low and high into the `a` and `b` columns of the `t` table.

```sql
CALL insertSampleData(10000,1,1000);
```

```sql
EXPLAIN SELECT 
    *
FROM
    t
ORDER BY a , b; -- use index a_asc_b_asc
```

```sql
EXPLAIN SELECT 
    *
FROM
    t
ORDER BY a , b DESC; -- use index a_asc_b_desc
```

```sql
EXPLAIN SELECT 
    *
FROM
    t
ORDER BY a DESC , b; -- use index a_desc_b_asc
```

```sql
EXPLAIN SELECT 
    *
FROM
    t
ORDER BY a DESC , b DESC; -- use index a_desc_b_desc
```

## Composite index

A composite index is an index on multiple columns. MySQL allows you to create a composite index that consists up to 16 columns.

A composite index is also known as a multiple-column index.

The query optimizer uses the composite indexes for queries that test all columns in the index, or queries that test the first columns, the first two columns, and so on.

To create a composite index at the time of table creation, you use the following statement:

```sql
CREATE TABLE table_name (
    c1 data_type PRIMARY KEY,
    c2 data_type,
    c3 data_type,
    c4 data_type,
    INDEX index_name (c2,c3,c4)
);
```

In this syntax, the composite index consists of three columns c2, c3, c4.

Or you can add a composite index to an existing table by using the `CREATE INDEX` statement:

```sql
CREATE INDEX index_name 
ON table_name(c2,c3,c4);
```

Notice that if you have a composite index on (c1, c2, c3), you will have indexed search capabilities on one the following column combinations:

```
(c1)
(c1,c2)
(c1,c2,c3)
```

```sql
SELECT
    *
FROM
    table_name
WHERE
    c1 = v1;
 
 
SELECT
    *
FROM
    table_name
WHERE
    c1 = v1 AND 
    c2 = v2;
 
 
SELECT  
    *
FROM
    table_name
WHERE
    c1 = v1 AND 
    c2 = v2 AND 
    c3 = v3;
```

The query optimizer cannot use the index to perform lookups if the columns do not form a leftmost prefix of the index. For example the following queryies cannot use the composite for lookups:

```sql
SELECT
    *
FROM
    table_name
WHERE
    c1 = v1 AND 
    c3 = v3;
```

### Composite index example

We will use the employees table which consist of following columns - employeeNumber, lastName, firstName, extension, email, officeCode, reportsTo, jobTitle.

The following statement creates a composite index over the `lastName` and `firstName` columns.

```sql
CREATE INDEX name
ON employees(lastName, firstName);
```

First, the name index can be used for lookups in the queries that specify a lastName value because the lastname column is the leftmost prefix of the index.

Second, the `name` index can be used for queries that specify values for the combination of the `lastName` and `firstName` values.

The `name` index, therefore, is used for lookups in the following queries:

1. Find employees whose last name is `Patterson`
2. Find employees whose last name is `Patterson` and first name is `Steve`
3. Find employees whose last name is `Patterson` and first name is `Steve` or `Mary`.

## Clustered Index

Typically, an index is a separate data structure such as B-Tree that stores the key values used for faster lookups.

A clustered index, on the other hand is actually the table. It is an index that enforces the ordering on the rows of the table physically.

Once a clustered index is created, all rows in the table will be stored according to the key columns used to create the clustered index.

Because a clustered index store the rows in a stored order, each table have only one clustered index.

### Clustered indexes on InnoDB tables

Each InnoDB table requires clustered index. The clustered index helps an InnoDB table optimize data manipulations such as `SELECT`, `INSERT`, `UPDATE` and `DELETE`.

When you define a primary key for an InnoDB table, MySQL uses the primary key as the clustered index.

If you do not have a primary key for the table, MySQL will search for the first `UNIQUE` index where all the key columns are `NOT NULL` and use this `UNIQUE` index as the clustered index.

In case the InnoDB table has no primary key or suitable `UNIQUE` index, MySQL internally generates a hidden clustered index named `GEN_CLIST_INDEX` on a synthetic column which contains the row ID values.

As the result, each InnoDB table always has one and only one clustered index.

All indexes other than the clustered index are the non-clusteered indexes or secondary indexes.In InnoDB tables, each record in the secondary index contains the primary key columns for the row as well as the columns specified in the non-clustered index. MySQL uses this primary key value for the row lookups in the clustered index.

Therefore, it is advantageous to have a short primary key otherwise, the secondary indexes will use more space. Typically, the auto-increment integer column is used for the primary key column.

## Index cardinality

Index cardinality refers to the uniqueness of values stored in a specified column within an index.

MySQL generates the index cardinality to generate an optimal query plan for a given query. It also uses the index cardinality to decide whether to use the index or not in the join operations.

If the query optimizer chooses the index with a low cardinality, it may be more effective to scan rows without using the index.

To view the index cardinality, you can use the `SHOW INDEXES` command.

For example, the following statement returns the index information of the `orders` table in the sample database with the cardinality:

```sql
mysql> SHOW INDEXES FROM orders;
+--------+------------+----------------+--------------+----------------+-----------+-------------+----------+--------+------+------------+---------+---------------+---------+
| Table  | Non_unique | Key_name       | Seq_in_index | Column_name    | Collation | Cardinality | Sub_part | Packed | Null | Index_type | Comment | Index_comment | Visible |
+--------+------------+----------------+--------------+----------------+-----------+-------------+----------+--------+------+------------+---------+---------------+---------+
| orders |          0 | PRIMARY        |            1 | orderNumber    | A         |         326 |     NULL |   NULL |      | BTREE      |         |               | YES     |
| orders |          1 | customerNumber |            1 | customerNumber | A         |          98 |     NULL |   NULL |      | BTREE      |         |               | YES     |
+--------+------------+----------------+--------------+----------------+-----------+-------------+----------+--------+------+------------+---------+---------------+---------+
2 rows in set (0.01 sec)
```

In the output, the `PRIMARY KEY` for the `orderNumber` column shows the table has 326 unique values, while the `custmerNaumber` column only has 98 distinct values.

As mentioned earlier, index statistics are only approximate and may not represent the real size of the rows in the table. To generate more accurate statistical information, you use the `ANALYZE TABLE` command.

## USE INDEX Hint

In MySQL, when you submit an SQL query, the query optimizer will try to make an optimal query execution plan. 

To determine the best possible plan, the query optimizer makes use of many parameters. One of the most important parameters for choosing which index to use is stored key distribution which is also known as cardinality.

The cardinality, however, may be not accurate for example in case the table ghas been modified heavily with many inserts or deletes.

To solve this issue, you should run the `ANALYZE TABLE` statement periodically to update the cardinality.

In addition, MySQL provides an alternative way that allows you to recomment the indexes that the query optimizer should by using an index hind called `USE INDEX`.

The following illustrates syntax of the MySQL `USE INDEX` hint:

```sql
SELECT select_list
FROM table_name USE INDEX(index_list)
WHERE condition;
```

In this syntax, the `USE INDEX` instructs the query optimizer to use one of the named indexes to find rows in the table.

Notice that when you recomment the indexes to use, the query optimizer may either decide to use them or not depending on the query plan that it comes up with.

## Force Index

The query optimizer is a component in the MySQL database server that makes the most optional execution plan for an SQL statement.

The query optimizer uses the available statistics to come up with the plan that has the lowest cost among all candidate plans.

For example, a query migh request for products whose prices are betweeen 10 and 80. If the statistics show that 80% of products have these price ranges, then it may decide that a full table scan is the most efficient. However if statistics show that very few products have these price ranges, then reading an index followed by a table access could be faster and more efficient that a full table scan.

In case the query optimizer ignores the index, you can use the `FORCE INDEX` hint to instruct it to use the index instead.

The following illustrates the `FORCE INDEX` hint syntax:

```sql
SELECT * 
FROM table_name 
FORCE INDEX (index_list)
WHERE condition;
```

```sql
SELECT 
    productName, buyPrice
FROM
    products 
FORCE INDEX (idx_buyPrice)
WHERE
    buyPrice BETWEEN 10 AND 80
ORDER BY buyPrice;
```