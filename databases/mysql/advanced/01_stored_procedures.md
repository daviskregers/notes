# Stored procedures

Stored procedure is a segment of declarative SQL statements stored inside the database catalog. A stored procedure can be invoked by triggers, other stored procedures and applications.

A stored procedure that calls itself is known as a recursive stored procedure. Most database management systems support recursive stored procedures. However, MySQL does not support it very well. You should check your version of MySQL database before implementing them.

## Advantages of MySQL stored procedures

- Typically, stored procedures help increase performance of the applications. Once created, stored procedures are compiled and stored in the database. However, MySQL implements the stored procedures slightly different. Stored procedures are compiled on demand and then they are stored in procedure cache for every single connection. If an application uses a stored procedure multiple times in a single connection, the compiled version is used, otherwise, the stored procedure works like a query.

- Stored procedures help reduce the traffic between application and database server because instead of sending multiple lengthy SQL statements, the application has to send only the name and parameters of the stored procedure.

- Stored procedures are reusable and transparent to any applications. Stored procedures expose the database interface to all applications so that developers do not have to develop functions that already are supported in stored procedures.

- Stored procedures are secure. The database administrator can grant appropriate permissions to applications that access stored procedures in the database without giving any permissions on the underlying database tables.

## Disadvantages of MySQL stored procedures

- If you use many stored procedures, the memory usage of every connection that is using those stored procedures will increase substantially. In addition, if you overuse a large number of logical operations inside stored procedures, the CPU usage will increase because the database server is not well-designed for logical operations.

- Stored procedure's constructs are not designed for developing complex and flexible business logic.

- It is difficult to debug stored procedures. Only a few database management systems allow you to debug stored procedures. Unfortunetely, MySQL does not provide facilities for debugging stored procedures.

It is not easy to develop and maintain stored procedures. Developing and maintaining stored procedures are often required a specialized skill set that not all application developers possess. This may lead to problems in both application development and maintenance phases.

#  Writting and calling a stored procedure

```sql

DROP procedure IF EXISTS `GetAllProducts`;

DELIMITER //
 CREATE PROCEDURE GetAllProducts()
   BEGIN
   SELECT *  FROM products;
   END //
 DELIMITER ;
```

- The first command `DELIMITER //` is not related to the stored procedure syntax. It changes the standard delimiter from `;` to another. This is done in order to pass the stored procedure to the server as a whole rather than letting the `mysql` tool interpret each statement at a time. The `END` keyword ends the stored procedure. The `DELIMITER ;` reverts the default delimiter.

To call the stored procedure:

```sql
CALL GetAllProducts();
```

## Variables in stored procedures

A variable is a named data object whose value can change during the stored procedure execution. These variables are local to the stored procedure, must be declared before using it.

```sql
DECLARE variable_name datatype(size) DEFAULT default_value;
```

```sql
DECLARE x,y INT DEFAULT 0;
```

Assigning variables

```sql
DECLARE total_count INT DEFAULT 0;
SET total_count = 10;
```

Besides the `SET` statement, a `SELECT INTO` can be used to assign the result of a query.

```sql
DECLARE total_products INT DEFAULT 0;

SELECT 
    COUNT(*) INTO total_products
FROM products;
```

## Variable scope

A variable has it's own scope that defines it's lifetime. If you declare a variable inside a stored procedure, it will be out of scope when the `END` statement of stored procedure reaches.

If you declare a variable inside `BEGIN END` block, it will be out of scope if the END is reached. You can declare two or more variables with the same name in different scopes. 

A variable whose name begines with the `@` sign is a session variable. It is available and accessible until the session ends.

## Stored procedure parameters

In MySQL, a parameter has one of 3 modes: `IN`, `OUT` or `INOUT`.

- `IN` - is the default mode. When you define an `IN` parameter in a stored procedure, the calling program has to pass an argument to the stored procedure. In addition, the value of an `IN` parameter is protected. It means that event the value of the `IN` parameter is changed inside the stored procedure, it's original value is retained after the procedure ends.

- `OUT` - the value of an `OUT` parameter can be changed inside the stored procedure and it's new value is passed back to the calling program. Notice that stored procedure cannot access the initial value of the `OUT` parameter when it starts.

- `INOUT` - a combination of `IN` and `OUT` parameters. It means that the calling program may pass the argument, and the stored procedure can modify the parameter, then pass the new value back to the calling program.

```sql
MODE param_name param_type(param_size)
```

Each parameter is separated by a comm `,` if the stored procedure has more than one parameter.

```sql
DELIMITER //
CREATE PROCEDURE GetOfficeByCountry(IN countryName VARCHAR(255))
 BEGIN
 SELECT * 
 FROM offices
 WHERE country = countryName;
 END //
DELIMITER ;

CALL GetOfficeByCountry('USA');
```

```sql
DELIMITER $$
CREATE PROCEDURE CountOrderByStatus(
 IN orderStatus VARCHAR(25),
 OUT total INT)
BEGIN
 SELECT count(orderNumber)
 INTO total
 FROM orders
 WHERE status = orderStatus;
END$$
DELIMITER ;

CALL CountOrderByStatus('Shipped',@total);
SELECT @total;
```

```sql
DELIMITER $$
CREATE PROCEDURE set_counter(INOUT count INT(4),IN inc INT(4))
BEGIN
 SET count = count + inc;
END$$
DELIMITER ;

SET @counter = 1;
CALL set_counter(@counter,1); -- 2
CALL set_counter(@counter,1); -- 3
CALL set_counter(@counter,5); -- 8
SELECT @counter; -- 8
```

## Returning multiple values

```sql
DELIMITER $$
 
CREATE PROCEDURE get_order_by_cust(
 IN cust_no INT,
 OUT shipped INT,
 OUT canceled INT,
 OUT resolved INT,
 OUT disputed INT)
BEGIN
 -- shipped
 SELECT
            count(*) INTO shipped
        FROM
            orders
        WHERE
            customerNumber = cust_no
                AND status = 'Shipped';
 
 -- canceled
 SELECT
            count(*) INTO canceled
        FROM
            orders
        WHERE
            customerNumber = cust_no
                AND status = 'Canceled';
 
 -- resolved
 SELECT
            count(*) INTO resolved
        FROM
            orders
        WHERE
            customerNumber = cust_no
                AND status = 'Resolved';
 
 -- disputed
 SELECT
            count(*) INTO disputed
        FROM
            orders
        WHERE
            customerNumber = cust_no
                AND status = 'Disputed';
 
END

CALL get_order_by_cust(141,@shipped,@canceled,@resolved,@disputed);
SELECT @shipped,@canceled,@resolved,@disputed;
```