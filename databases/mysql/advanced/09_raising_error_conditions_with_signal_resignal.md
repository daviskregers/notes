# Raising Error condition with MySQL Signal / RESIGNAL statements

## MySQL SIGNAL Statements

You use the `SIGNAL` statement to return an error or warning condition to the caller from a stored program e.g. stored procedure, stored function, trigger or event. The `SIGNAL` statement provides you with control over which information for returning such as value and message `SQLSTATE`.

```sql
SIGNAL SQLSTATE | condition_name;
SET condition_information_item_name_1 = value_1,
    condition_information_item_name_1 = value_2, etc;
```

Following the `SIGNAL` keyword is a `SQLSTATE` value or a condition name declared by the `DECLARE CONDITION` statement. Notice that the `SIGNAL` statement must always specify a `SQLSTATE` value or a named condition that defined with an `SQLSTATE` value.

To provide the caller with information, you use the `SET` clause. If you want tot return multiple condition information item names with values, you need to separate each name/value pair by a comma.

The `condition_information_item_name` can be `MESSAGE_TEXT`, `MYSQL_ERRORNO`, `CURSOR_NAME` etc.

```sql
DELIMITER $$
 
CREATE PROCEDURE AddOrderItem(
          in orderNo int,
 in productCode varchar(45),
 in qty int, 
                         in price double, 
                         in lineNo int )
BEGIN
 DECLARE C INT;
 
 SELECT COUNT(orderNumber) INTO C
 FROM orders 
 WHERE orderNumber = orderNo;
 
 -- check if orderNumber exists
 IF(C != 1) THEN 
 SIGNAL SQLSTATE '45000'
 SET MESSAGE_TEXT = 'Order No not found in orders table';
 END IF;
 -- more code below
 -- ...
END
```

## MySQL RESIGNAL statement

Besides the `SIGNAL` statement, MySQL alsoprovides `RESIGNAL` statement used to raise a warning or error condition.

The `RESIGNAL` statement is similar to `SIGNAL` statement in term of functionality and syntax, except that:

- You must use the `RESIGNAL` statement within an error or warning handler, otherwise, you will get an error message saying that `RESIGNAL when handler is not active`. Notice that you can use `SIGNAL` statement anywhere inside a stored procedure.
- You can omit all attributes of the `RESIGNAL` statement, event the `SQLSTATE` value.

If you use the `RESIGNAL` statement, all attributes are the same as the ones passed to the condition handler.

```sql

DELIMITER $$
 
CREATE PROCEDURE Divide(IN numerator INT, IN denominator INT, OUT result double)
BEGIN
 DECLARE division_by_zero CONDITION FOR SQLSTATE '22012';
 
 DECLARE CONTINUE HANDLER FOR division_by_zero 
 RESIGNAL SET MESSAGE_TEXT = 'Division by zero / Denominator cannot be zero';
 -- 
 IF denominator = 0 THEN
 SIGNAL division_by_zero;
 ELSE
 SET result := numerator / denominator;
 END IF;
END

```