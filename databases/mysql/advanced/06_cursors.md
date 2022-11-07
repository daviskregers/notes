# MySQL Cursors

To handle a result set inside a stored procedure, you use a cursor. A cursor allows you to iterate a set of rows returned by a query and process each row accordingly.

MySQL cursor is read-only, non-scollable and asensitive.

- Read-only means that you cannot update data in the underlying table through the cursor.

- Non-scrollable means that you can only fetch rows in the order determined by the `SELECT` statement. You cannot fetch rows in the reversed order. You can't skip or jump to a specific row either.

- Asensitive means that there are two kinds of cursors - asensitive and insensitive cursors. Asensitive cursors point to the actual data, whereas an insensitive cursor uses a temporary copy of the data. An asensitive cursor performs faster than an insensitive cursor because it does not have to make a temporary copy of the data. However, any change that made to the data from other connections will affect the data.

The MySQL cursors can be used in stored procedures, stored function and triggers.

```sql
DECLARE cursor_name CURSOR FOR SELECT_statement;
```

The cursor declaration must be after any variable declaration. If you declare a cursor before variables declaration, MySQL will issue an error. A cursor must be associated wit a `SELECT` statemtn.

Next, you open the cursor by using the `OPEN` statemnt which initializes the result set for the cursor.

```sql
OPEN cursor_name;
```

Then you use `FETCH` statement to retrieve the next row pointed by the cursor and move the cursor to the next row in the result set.

```sql
FETCH cursor_name INTO variables list;
```

Finally, you call `CLOSE` statement to deactivate the cursor and release the memory.

```sql
CLOSE cursor_name;
```

When working with MySQL cursor, you must also declare a `NOT FOUND` handler to handle the situation when the cursor could not find any row. Because each time you call the `FETCH` statement, the cursor attempts to read the next row in the result set. 

```sql
DECLARE CONTINUE HANDLER FOR NOT FOUND SET finished = 1;
```

## Example

```sql

DELIMITER $$
 
CREATE PROCEDURE build_email_list (INOUT email_list varchar(4000))
BEGIN
 
 DECLARE v_finished INTEGER DEFAULT 0;
        DECLARE v_email varchar(100) DEFAULT "";
 
 -- declare cursor for employee email
 DEClARE email_cursor CURSOR FOR 
 SELECT email FROM employees;
 
 -- declare NOT FOUND handler
 DECLARE CONTINUE HANDLER 
        FOR NOT FOUND SET v_finished = 1;
 
 OPEN email_cursor;
 
 get_email: LOOP
 
 FETCH email_cursor INTO v_email;
 
 IF v_finished = 1 THEN 
 LEAVE get_email;
 END IF;
 
 -- build email list
 SET email_list = CONCAT(v_email,";",email_list);
 
 END LOOP get_email;
 
 CLOSE email_cursor;
 
END$$
 
DELIMITER ;


SET @email_list = "";
CALL build_email_list(@email_list);
SELECT @email_list;

```