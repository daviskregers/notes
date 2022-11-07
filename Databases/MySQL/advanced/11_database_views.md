# Database view

A database view is a virtual table or logical table which is defined as a SQL SELECT query with joins. Because a database view is similar to a database table, which consits of rows and columns, so you can query data against it. Most DBMS including MySQL allow you to update data in the underlying tables through the database view with some prerequesites.

## Advantages of database view

- A database view allows you to simplify complex queries: a database view is defined by an SQL statement that associates with many underlying tables. You can use database view to hide the complexity of underlying tables to the end-users and external applications. Though a tdatabase view, you only have to use simple SQL statements instead of complex ones with many joins.
- A database view helps limit database access to specific users. You may not want to subset of sensitive data can be query queryable by all users. You can use a database view to expose only non-sensitive data to a specific group of users.
- A database view provides extra security layer. Security is a vital part of any relational DBMS. The database view offers additional protection for a DBMS. The database view allows you to create the read-only view to expose read-only data to specific users. Users can only retrieve data in read-only view but cannot update it.
- A database view enables computed columns. A database table should not have calculated columns however a database view should. When you query data from the database view, the data of the computed column is calculated on the fly.
- A database view enables backward compatibility. 

## Disadvantages of database view

- Performance - querying data from a database view can be slow especially if the view is created on other views.
- Tables dependency - you can create a view based on underlying tables of the database. Whenever you change the structure of these tables that view is associated with, you have to change the view as well.

---

MySQL processes query against the views in two ways:

- MySQL creates a temporary table based on the view definition statement and executes the incoming query on this temporary table.
- MySQL combines the incoming query with the query defined the view into one query and executes the combined query.

MySQL supports versioning system for views. Each time when a view is altered or replaced, a copy of the view is back up in `arc` directory that resides in a specific database folder. The name of the backup file is `view_name.frm-00001`.

MySQL allows you to create a view based on other views. In other words, you can refer to other views in the SELECT statement which defines the view.

## View restrictions

You cannot create an index on a view. MySQL uses indexes of the underlying tables when you query data against the views that use the merge algorithm. For the views that use the `temptable` algorithm, indexes are not utilized when you query data against the views.

You cannot use subqueryies in the `FROM` clause of the `SELECT` statement. that defines the view before MySQL 5.7.7.

If you drop or rename tables to which view references, MySQL does not issue any error. However, MySQL does invalidate the view. You can use the `CHECK TABLE` statement to check whether the view is valid or not.

A simple view can be updatable. A view created based on a complex `SELECT` satement with join, subquery, etc. cannot be updatable.

MySQL does not support materialized view like other DBMS like Oracle, PostgreSQL.

## Creating Views

```sql
CREATE 
   [ALGORITHM = {MERGE  | TEMPTABLE | UNDEFINED}]
VIEW view_name [(column_list)]
AS
select-statement;
```

The algorithm attribute allows you to control which mechanism MySQL uses when creating the view. MySQL provides three algorithms: `MERGE`, `TEMPTABLE`, and `UNDEFINED`.

- Using `MERGE` algorithm, MySQL first combines the input query with the SELECT statement, which defines the view, into a single query. And then MySQL executes the combined query to return the result set. The `MERGE` algorithm is not allowed if the `SELECT` statement contains aggregate function like MIN, MAX, SUM, COUNT, AVG or DISTINCT, GROUP BY, HAVING, LIMIT, UNION, UNION ALL, subquery. In case the SELECT statement refers to no table, the MERGE algorithm is also not allowed. If the `MERGE` algorithm is not allowed, MySQL changes the algorithm to `UNDEFINED`. Note that the combination of input query and the query in the view definition into one query is reffered to as view resolution.
- Using `TEMPTABLE` algorithm, MySQL first creates a temporary table based on the `SELECT` statement that defines the view, and then it executes the input query against this temporary table. Because MySQL has to create a temporary table to store the result set and moves the data from the base tables to the temporary table, the `TEMPTABLE` algorithm is less efficient than the `MERGE` algorithm. In addition, a view that uses `TEMPTABLE` algorithm is not updatable.
- The `UNDEFINED` is the default algorithm when you create a view without specifying an explicit algorithm. The `UNDEFINED` algorithm lets MySQL make a choice of using `MERGE` or `TEMPTABLE` algorithm. MySQL prefers `MERGE` to `TEMPTABLE` algorithm because the `MERGE` is much more efficient.

## View name

Within a database, views and tables share the same namespace, therefore, a view and a table cannot have the same name. In addition, the name of a view must follow the table's naming rules.

## SELECT statement

In the `SELECT` statement, you can query data from any table or view that exists in the database. 

- The SELECT statement can contain a subquery in WHERE clause but not in the FROM clause.
The SELECT statement cannot refer to any variables including local variables, user variables, and session variables.
- The SELECT statement cannot refer to the parameters of prepared statements.

## Creating view examples

```sql
CREATE VIEW SalePerOrder AS
    SELECT 
        orderNumber, SUM(quantityOrdered * priceEach) total
    FROM
        orderDetails
    GROUP by orderNumber
    ORDER BY total DESC;
```

```sql
SELECT 
    *
FROM
    salePerOrder;
```

## Creating view based on another view

```sql
CREATE VIEW BigSalesOrder AS
    SELECT 
        orderNumber, ROUND(total,2) as total
    FROM
        saleperorder
    WHERE
        total > 60000;
```

```sql
SELECT 
    orderNumber, total
FROM
    BigSalesOrder;
```

## Creating views with joins

```sql
CREATE VIEW customerOrders AS
    SELECT 
        d.orderNumber,
        customerName,
        SUM(quantityOrdered * priceEach) total
    FROM
        orderDetails d
            INNER JOIN
        orders o ON o.orderNumber = d.orderNumber
            INNER JOIN
        customers c ON c.customerNumber = c.customerNumber
    GROUP BY d.orderNumber
    ORDER BY total DESC;
```

```sql
SELECT
    *
FROM
    customerOrders;
```

## Creating views with a subquery

```sql
CREATE VIEW aboveAvgProducts AS
    SELECT 
        productCode, productName, buyPrice
    FROM
        products
    WHERE
        buyPrice > 
 (SELECT 
                AVG(buyPrice)
            FROM
                products)
    ORDER BY buyPrice DESC;
```

```sql
SELECT 
    *
FROM
    aboveAvgProducts;

```

## Creating updatable views

In MySQL, views are not only query-able but also updatable. It means that you can use INSER or UPDATE statement to insert or update rows of the base table through the updatable view. In addition, you can use DELETE statement to remove rows of the underlying table through view.

However, to create an updatable view, the SELECT statement that defines the view must not contain any of the following elements:

- Aggregate functions such as MIN, MAX, SUM, AVG and COUNT.
- DISTINCT
- GROUP BY
- HAVING
- UNION or UNION ALL
- Left join or Outer join
- Reference to non-updatable view in the FROM clause
- Reference only to literal values
- Multiple references to any column of the base table.

If you create a view with the `TEMPTABLE` algorithmm you cannot update the view.

```sql
CREATE VIEW officeInfo
 AS 
   SELECT officeCode, phone, city
   FROM offices;
```

```sql
SELECT 
    *
FROM
    officeInfo;
```

```sql
UPDATE officeInfo 
SET 
    phone = '+33 14 723 5555'
WHERE
    officeCode = 4;
```

## Checking the updatable view information

You can check if a view in a database is updatable by querying the is_updatable column from the views table in the information_schema database.

```sql
SELECT 
    table_name, 
    is_updatable
FROM
    information_schema.views
WHERE
    table_schema = 'classicmodels';
```

## Removing rows through a view

```sql
-- create a new table named items
CREATE TABLE items (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    price DECIMAL(11 , 2 ) NOT NULL
);
 
-- insert data into the items table
INSERT INTO items(name,price) 
VALUES('Laptop',700.56),('Desktop',699.99),('iPad',700.50) ;
 
-- create a view based on items table
CREATE VIEW LuxuryItems AS
    SELECT 
        *
    FROM
        items
    WHERE
        price > 700;
-- query data from the LuxuryItems view
SELECT 
    *
FROM
    LuxuryItems;

DELETE FROM LuxuryItems 
WHERE
    id = 3;

```

## Ensuring view consistency with the `CHECK OPTION` clause

Somtimes, you create a view to reveal the partial data of a table only. However, a simple view is updatable therefore it is possible to update data which is not visible through the view. This update makes the view inconsistent. To ensure the consistency of the view, you use the `WITH CHECK OPTION` clause when you create or modify the view.

It is an optional part of the `CREATE VIEW` statement. The `WITH CHECK OPTION` clause prevents you from updating or inserting rows that are not visible through the view. In other words, whether you update or insert a row of the base table through a view, MySQL ensures that the insert or update operation is conformed with the definition of the view.

```sql
CREATE OR REPLACE VIEW view_name 
AS
  select_statement
  WITH CHECK OPTION;
```

## Understanding LOCAL & CASCADED in WITH CHECK OPTION Clause

When you create a view with the `WITH CHECK OPTION` clause, MySQL checks every row that is being changed through the view e.g., insert, update, delete, to make it conformable to the view's definition. Because MySQL allows a view to be created based on another view, it also checks the rules in dependent views for consistency. 

To determine the scope of check, MySQL provides two options: `LOCAL` and `CASCADED`. By default it uses `CASCADED` scope.

If a view uses a `WITH LOCAL CHECK OPTION`, MySQL checks the rules of views that have a `WITH LOCAL CHECK OPTION` and a `WITH CASCADED CHECK OPTION`. 

If a view uses `WITH CASCADED CHECK OPTION`, MySQL checks the rules of all dependent views.

## Managiung views

### Showing view definition

```sql
SHOW CREATE VIEW [database_name].[view_ name];
```

```sql
CREATE VIEW organization AS
    SELECT 
        CONCAT(E.lastname, E.firstname) AS Employee,
        CONCAT(M.lastname, M.firstname) AS Manager
    FROM
        employees AS E
            INNER JOIN
        employees AS M ON M.employeeNumber = E.ReportsTo
    ORDER BY Manager;

SHOW CREATE VIEW organization;
```

You can also display the definition of the view using any plain text editior to open the view definition file in the database folder. 

For example, to open the organization view definition, you can find the view definition file with the following path:

`\data\database\organization.frm`

You should probably not modify the file.

### Modify the views

```sql
ALTER
 [ALGORITHM =  {MERGE | TEMPTABLE | UNDEFINED}]
  VIEW [database_name].  [view_name]
   AS 
 [SELECT  statement]
```

```sql
ALTER VIEW organization
  AS 
  SELECT CONCAT(E.lastname,E.firstname) AS Employee,
         E.email AS  employeeEmail,
         CONCAT(M.lastname,M.firstname) AS Manager
  FROM employees AS E
  INNER JOIN employees AS M
    ON M.employeeNumber = E.ReportsTo
  ORDER BY Manager;
```

```sql
CREATE OR REPLACE VIEW contacts AS
    SELECT 
        firstName, lastName, extension, email
    FROM
        employees;
```

```sql
CREATE OR REPLACE VIEW contacts AS
    SELECT 
        firstName, 
        lastName, 
        extension, 
        email, 
        jobtitle
    FROM
        employees;
```

### Removing views

```sql
DROP VIEW [IF EXISTS] [database_name].[view_name]
```

```sql
DROP VIEW IF EXISTS organization;
```

Each time you modify or remove a view, MySQL makes a backup of the view definition file to the `/database_name/arc/` folder. 