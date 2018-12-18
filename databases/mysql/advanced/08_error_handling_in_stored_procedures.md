# Handling errors in Stored Procedures

When an error occurs inside a stored procedure, it is important to handle it appropriately, such as continuing or exiting the current code block's execution, and issuing a meaningful error message.

## Declaring a handler

```sql
DECLARE action HANDLER FOR  condition_value statement;
```

If a condition whose value matches the `condition_value`, MySQL will execute the statement and continue or exit the current code block based on the `action`.

The `action` accepts one of following values:

- `CONTINUE` - the execution of enclosing code in block continues.
- `EXIT` - the execution of the enclosing block where the handler is declared is terminated.

The `condition_value` specifies a particular condition or a class of condition that activate the handler. The `condition_value` accepts one of the following values:

- A MySQL error code.
- A standard `SQLSTATE` value. Or it can be an `SQLWARNING`, `NOTFOUND` or `SQLEXCEPTION` condition, which is shorthand for the class of `SQLSTATE` values. The `NOTFOUND` condition is used for a cursor or `SELECT INTO variable_list` statement.
- A named condition associated with either a MySQL error code or `SQLSTATE` value.

The statement could be a simple statement or compound statement enclosing by the `BEGIN` and `END` keywords.

Handler for `SQLEXCEPTION`

```sql
DECLARE CONTINUE HANDLER FOR SQLEXCEPTION SET has_error = 1;
```

```sql
DECLARE EXIT HANDLER FOR SQLEXCEPTION
BEGIN
ROLLBACK;
SELECT 'An error has occurred, operation rollbacked and the stored procedure was terminated';
END;
```

Handler for `NOTFOUND`

```sql
DECLARE CONTINUE HANDLER FOR NOT FOUND SET no_row_found = 1;
```

Handler for error code 1062 - duplicate key.

```sql
DECLARE CONTINUE HANDLER FOR 1062
SELECT 'Error, duplicate key occurred';
```

Example in a stored procedure

```sql
DELIMITER $$
 
CREATE PROCEDURE insert_article_tags(IN article_id INT, IN tag_id INT)
BEGIN
 
 DECLARE CONTINUE HANDLER FOR 1062
 SELECT CONCAT('duplicate keys (',article_id,',',tag_id,') found') AS msg;
 
 -- insert a new record into article_tags
 INSERT INTO article_tags(article_id,tag_id)
 VALUES(article_id,tag_id);
 
 -- return tag count for the article
 SELECT COUNT(*) FROM article_tags;
END

CALL insert_article_tags(1,1);
CALL insert_article_tags(1,2);
CALL insert_article_tags(1,3);
CALL insert_article_tags(1,3);
```

```sql
DELIMITER $$
 
CREATE PROCEDURE insert_article_tags_2(IN article_id INT, IN tag_id INT)
BEGIN
 
 DECLARE EXIT HANDLER FOR SQLEXCEPTION 
 SELECT 'SQLException invoked';
 
 DECLARE EXIT HANDLER FOR 1062 
        SELECT 'MySQL error code 1062 invoked';
 
 DECLARE EXIT HANDLER FOR SQLSTATE '23000'
 SELECT 'SQLSTATE 23000 invoked';
 
 -- insert a new record into article_tags
 INSERT INTO article_tags(article_id,tag_id)
   VALUES(article_id,tag_id);
 
 -- return tag count for the article
 SELECT COUNT(*) FROM article_tags;
END
```

## MySQL handler precedence

In case there are multiple handlers that are eligible for handling an error, MySQL will call the most specific handler to handle the error first.

```sql
DELIMITER $$
 
CREATE PROCEDURE insert_article_tags_3(IN article_id INT, IN tag_id INT)
BEGIN
 
 DECLARE EXIT HANDLER FOR 1062 SELECT 'Duplicate keys error encountered';
 DECLARE EXIT HANDLER FOR SQLEXCEPTION SELECT 'SQLException encountered';
 DECLARE EXIT HANDLER FOR SQLSTATE '23000' SELECT 'SQLSTATE 23000';
 
 -- insert a new record into article_tags
 INSERT INTO article_tags(article_id,tag_id)
 VALUES(article_id,tag_id);
 
 -- return tag count for the article
 SELECT COUNT(*) FROM article_tags;
END

CALL insert_article_tags_3(1,3);
```

You will see that the MySQL error code handler will be called.

## Using a named error condition

```sql
DECLARE table_not_found CONDITION for 1051;
 
DECLARE EXIT HANDLER FOR table_not_found 
SELECT 'Please create table abc first';
 
SELECT * FROM abc;
```

Notice that the condition declaration must appear before handler or cursor declarations.