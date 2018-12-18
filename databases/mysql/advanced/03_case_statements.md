

# MySQL CASE statement

There are two forms of the `CASE` statements - simple and searched `CASE` statements.

## Simple CASE statement

```sql
CASE  case_expression
   WHEN when_expression_1 THEN commands
   WHEN when_expression_2 THEN commands
   ...
   ELSE commands
END CASE;
```

You use it to check the value of an expression agains a set of unique values.

```sql
DELIMITER $$
 
CREATE PROCEDURE GetCustomerShipping(
 in  p_customerNumber int(11), 
 out p_shiping        varchar(50))
BEGIN
    DECLARE customerCountry varchar(50);
 
    SELECT country INTO customerCountry
 FROM customers
 WHERE customerNumber = p_customerNumber;
 
    CASE customerCountry
 WHEN  'USA' THEN
    SET p_shiping = '2-day Shipping';
 WHEN 'Canada' THEN
    SET p_shiping = '3-day Shipping';
 ELSE
    SET p_shiping = '5-day Shipping';
 END CASE;
END$$

SET @customerNo = 112;
 
SELECT country into @country
FROM customers
WHERE customernumber = @customerNo;
 
CALL GetCustomerShipping(@customerNo,@shipping);
 
SELECT @customerNo AS Customer,
       @country    AS Country,
       @shipping   AS Shipping;

```

## Searched CASE statement

The simple `CASE` statement only allows you match a value of an expression against a set of distinct values. In order to perform more complex matches such as ranges, you use the searched `CASE` statement. It is equivalent to the `IF` statement, however it's construct is much more readable.

```sql
CASE
    WHEN condition_1 THEN commands
    WHEN condition_2 THEN commands
    ...
    ELSE commands
END CASE;
```

```sql
DELIMITER $$
 
CREATE PROCEDURE GetCustomerLevel(
 in  p_customerNumber int(11), 
 out p_customerLevel  varchar(10))
BEGIN
    DECLARE creditlim double;
 
    SELECT creditlimit INTO creditlim
 FROM customers
 WHERE customerNumber = p_customerNumber;
 
    CASE  
 WHEN creditlim > 50000 THEN 
    SET p_customerLevel = 'PLATINUM';
 WHEN (creditlim <= 50000 AND creditlim >= 10000) THEN
    SET p_customerLevel = 'GOLD';
 WHEN creditlim < 10000 THEN
    SET p_customerLevel = 'SILVER';
 END CASE;
 
END$$

CALL GetCustomerLevel(112,@level);
SELECT @level AS 'Customer Level';
```