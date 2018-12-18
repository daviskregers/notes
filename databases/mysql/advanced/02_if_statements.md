# MySQL IF Statement

The MySQL allows you to execute a set of SQL statements based on a certain condiftion or value of an expression. 

```sql
IF expression THEN 
   statements;
END IF;
```

If the expression evaluates to `TRUE`, then the statements will be executed.

# MySQL IF-ELSE

```sql
IF expression THEN
   statements;
ELSE
   else-statements;
END IF;
```

# MySQL IF-ELSEIF-ELSE

```sql
IF expression THEN
   statements;
ELSEIF elseif-expression THEN
   elseif-statements;
...
ELSE
   else-statements;
END IF;
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
 
    IF creditlim > 50000 THEN
 SET p_customerLevel = 'PLATINUM';
    ELSEIF (creditlim <= 50000 AND creditlim >= 10000) THEN
        SET p_customerLevel = 'GOLD';
    ELSEIF creditlim < 10000 THEN
        SET p_customerLevel = 'SILVER';
    END IF;
 
END$$

```