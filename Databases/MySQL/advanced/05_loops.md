# MySQL Lopp in stored procedures

MySQL provides loop statements that allow you to execute a block of SQL code repeatedly based on a condition. There are three loop statements in MySQL - `WHILE`, `REPEAT` and `LOOP`.

## While Loop

```sql
WHILE expression DO
   statements
END WHILE
```

```sql
DELIMITER $$
 DROP PROCEDURE IF EXISTS test_mysql_while_loop$$
 CREATE PROCEDURE test_mysql_while_loop()
 BEGIN
 DECLARE x  INT;
 DECLARE str  VARCHAR(255);
 
 SET x = 1;
 SET str =  '';
 
 WHILE x  <= 5 DO
 SET  str = CONCAT(str,x,',');
 SET  x = x + 1; 
 END WHILE;
 
 SELECT str;
 END$$
DELIMITER ;

CALL test_mysql_while_loop();
```

## REPEAT loop

```sql
REPEAT
 statements;
UNTIL expression
END REPEAT
```

```sql
DELIMITER $$
 DROP PROCEDURE IF EXISTS mysql_test_repeat_loop$$
 CREATE PROCEDURE mysql_test_repeat_loop()
 BEGIN
 DECLARE x INT;
 DECLARE str VARCHAR(255);
        
 SET x = 1;
        SET str =  '';
        
 REPEAT
 SET  str = CONCAT(str,x,',');
 SET  x = x + 1; 
        UNTIL x  > 5
        END REPEAT;
 
        SELECT str;
 END$$
 DELIMITER ;

CALL mysql_test_repeat_loop();
 ```

 ## LOOP, LEAVE and ITERATE statements

 There are two statements that allow you to control the loop:

 - The `LEAVE` statement allow you to exit the loop immediately without waiting for checking the condition. The `LEAVE` statement works like the `break` statement in other languages.

 - The `ITERATE` statement allows you to skip the endire code under it and start a new iteration. Similar to `continue` in other languages.

## LOOP statement

 ```sql
CREATE PROCEDURE test_mysql_loop()
 BEGIN
 DECLARE x  INT;
        DECLARE str  VARCHAR(255);
        
 SET x = 1;
        SET str =  '';
        
 loop_label:  LOOP
 IF  x > 10 THEN 
 LEAVE  loop_label;
 END  IF;
            
 SET  x = x + 1;
 IF  (x mod 2) THEN
 ITERATE  loop_label;
 ELSE
                SET  str = CONCAT(str,x,',');
 END  IF;
         END LOOP;    
 
         SELECT str;
 
 END;
 ```