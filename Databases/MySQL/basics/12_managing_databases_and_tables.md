# Managing databases and tables

# Managing a database

Use / select database

```sql
USE database_name
```

Get the name of currently selected database

```sql
SELECT database()
```

Create database

```sql
CREATE DATABASE [IF NOT EXISTS] database_name
[CHARACTER SET character_set]
[COLLATE collation_name];
```

Displaying databases

```sql
SHOW DATABASES
```

Removing database

```sql
DROP DATABASE [IF EXISTS] database_name;
```

# Tables

Create table

```sql
CREATE TABLE IF NOT EXISTS tasks (
    task_id INT AUTO_INCREMENT,
    title VARCHAR(255) NOT NULL,
    start_date DATE,
    due_date DATE,
    status TINYINT NOT NULL,
    priority TINYINT NOT NULL,
    description TEXT,
    PRIMARY KEY (task_id)
)  ENGINE=INNODB;
```

Alter table

```sql
ALTER TABLE tasks
CHANGE COLUMN task_id task_id INT(11) NOT NULL AUTO_INCREMENT;
```
```sql
ALTER TABLE tasks 
ADD COLUMN complete DECIMAL(2,1) NULL
AFTER description;
```
```sql
ALTER TABLE tasks
DROP COLUMN description;
```
```sql
ALTER TABLE tasks
RENAME TO work_items;
```

Drop table

```sql
DROP [TEMPORARY] TABLE [IF EXISTS] table_name [, table_name] ...
[RESTRICT | CASCADE]
```

Temporary table

```sql
CREATE TEMPORARY TABLE top10customers
SELECT p.customerNumber, 
       c.customerName, 
       ROUND(SUM(p.amount),2) sales
FROM payments p
INNER JOIN customers c ON c.customerNumber = p.customerNumber
GROUP BY p.customerNumber
ORDER BY sales DESC
LIMIT 10;
```

```sql
DROP TEMPORARY TABLE top10customers;
```