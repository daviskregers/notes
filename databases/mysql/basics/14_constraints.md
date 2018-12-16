# Constraints

## NOT NULL Constraint

The `NOT NULL` constraint is a column constraint that forces the values of a column to non-NULL values only.

```sql
CREATE TABLE tasks (
    id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    start_date DATE NOT NULL,
    end_date DATE
);
```

```sql
ALTER TABLE tasks 
CHANGE end_date end_date DATE NOT NULL;
```

Verify change
```sql
DESCRIBE tasks;
```

## Primary key

A primary key is a column or a set of columns that uniquely identifies each row in the table. You must follow the rules below when you define a primary key for a table:

- Primary key must contain unique values. If the primary key consists of multiple columns, the combination of values in these columns must be unique.
- A primary key column cannot contain NULL values. It means that you have to declare primary key column with the `NOT NULL` attribute. I f you dont, MySQL will force the primary key column as `NOT NULL` implicitly.
- A table has only one primary key.

Because MySQL works faster with integers, the data type of the primary key columns should be integer. However, you should make sure that the value ranges of the integer type for the primary key is sufficient for storing all possible rows that table may have.

A primary key often has `AUTO_INCREMENT` attribute that generates a unique sequence for the key automatically.

```sql
CREATE TABLE users(
   user_id INT AUTO_INCREMENT PRIMARY KEY,
   username VARCHAR(40),
   password VARCHAR(255),
   email VARCHAR(255)
);
```

```sql
CREATE TABLE roles(
   role_id INT AUTO_INCREMENT,
   role_name VARCHAR(50),
   PRIMARY KEY(role_id)
);
```

```sql
ALTER TABLE table_name
ADD PRIMARY KEY(primary_key_column);
```

## Foreign key 

A foreign key is a field in a table that matches another field of another table. A freign key places constraints on data in the related tables.

```sql
ALTER TABLE products
ADD FOREIGN KEY fk_vendor(vdr_id)
REFERENCES vendors(vdr_id)
ON DELETE NO ACTION
ON UPDATE CASCADE;
```

```sql
ALTER TABLE table_name 
DROP FOREIGN KEY constraint_name;
```

```sql
CREATE TABLE products (
  prd_id int(11) NOT NULL AUTO_INCREMENT,
  prd_name varchar(355) NOT NULL,
  prd_price decimal(10,0) DEFAULT NULL,
  cat_id int(11) NOT NULL,
  vdr_id int(11) NOT NULL,
  PRIMARY KEY (prd_id),
  KEY fk_cat (cat_id),
  KEY fk_vendor(vdr_id),
 
  CONSTRAINT products_ibfk_2 
  FOREIGN KEY (vdr_id) 
  REFERENCES vendors (vdr_id) 
  ON DELETE NO ACTION 
  ON UPDATE CASCADE,
 
  CONSTRAINT products_ibfk_1 
  FOREIGN KEY (cat_id) 
  REFERENCES categories (cat_id) 
  ON UPDATE CASCADE
) ENGINE=InnoDB;
```

Disable foreign key checks
```sql
SET foreign_key_checks = 0;
```

## Unique constraint

The UNIQUE constraint is either column constraint or table constraint that defines a rule that constraints values in a column or a group of columns to be unique.

```sql
CREATE TABLE table_1(
 
   ...
   column_name_1 data_type,
   column_name_2 data type,
   ...
   UNIQUE(column_name_1,column_name_2)
);
```

```sql
CREATE TABLE table_1(
   ...
   column_name_1 data_type,
   column_name_2 data type,
   ...
   CONSTRAINT constraint_name UNIQUE(column_name_1,column_name_2)
);
```



