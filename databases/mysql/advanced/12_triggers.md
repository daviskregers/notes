# MySQL triggers

A SQL trigger is a special type of a stored procedure. Special because it is not called directly like a stored procedure but instead it is triggered automatically when data modification event is made against a table.

## Advantages of SQL triggers

- SQL triggers provide an alternative way tto check the integrity of data.
- SQL triggers can catch errors in business logic in the database layer
- SQL triggers provide an alternative way to run scheduled tasks. By using SQL triggers, you don't have to wait to run the scheduled tasks because triggers are invoked automatically before or after a change is made to the data in the tables.
- SQL triggers are very useful to audit the changes of data in tables.

## DIsadvantages of SQL triggers

- SQL triggers only can provide an extended validation and they cannot replace all the validations. Some simple validations have to be done in the application layer. For example, you can validate user's inputs in the client side by using JavaScript.
- SQL triggers are invoked  and executed invisible from the client applications, therefore, it is difficult to figure out what happens in the database layer.
- SQL triggers increase the overhead of the database server.

## MySQL triggers

In MySQL, a trigger is a set of SQL statements that is invoked automatically when a change is made to the data on the associated table. A trigger can be defined to be invoded either before or after the data is changed by `INSERT`, `UPDATE` or `DELETE` statement. Before MySQL version 5.7.2, you can define maximum of 6 triggers for each table.

- `BEFORE INSERT`
- `AFTER INSERT`
- `BEFORE UPDATE`
- `AFTER UPDATE`
- `BEFORE DELETE`
- `AFTER DELETE`

However, from MySQL version 5.7.2, you can define multiple triggers for the same trigger event and action time.

When you use a statement that does not use `INSER`, `DELETE` or `UPDATE` statement to change data in a table, the triggers associated with the table are not invoked. For example, the `TRUNCATE` statement removes all data of a table but does not invoke the trigger associated with that table.

There are some statements that use the `INSERT` statement behind the scenes such as `REPLACE` or `LOAD DATA`. If you use these statements, the correstponding triggers associated the tables are invoked.

YOu must use a unique name for each trigger associated with a table. However, you can have the same trigger name defined for different tables through it is a good practice.

You should name the triggers using the following convention:

```sql
(BEFORE | AFTER)_tableName_(INSERT|UPDATE|DELETE)
```
For example, `before_order_update` is a trigger invoked before a row in the order table is updated.

```sql
tableName_(BEFORE|AFTER)_(INSERT|UPDATE|DELETE)
```

## MySQL trigger storage

MySQL stores triggers in a data directory e.g. `/data/classicmodels/` with the files named `tablename.TRG` and `triggername.TRN`:
- The `tablename.TRG` file maps the trigger to corresponding table.
- the `triggername.TRN` file contains the trigger definition.

You can back up the MySQL triggers by copying trigger files to the backup folder. You can also backup the triggers using the mysqldumptool.

## MySQL trigger limitations

MySQL triggers cover all features defined in the standard SQL. However, there are some limitations that you should know before using them in your applications.

MySQL triggers cannot:

- Use `SHOW`, `LOAD DATA`, `LOAD TABLE`, `BACKUP DATABASE`, `RESTORE`, `FLUSH` and `RETURN` statements.
- Use statements that commit or rollback implicity or explicity such as `COMMIT`, `ROLLBACK`, `START TRANSACTION`, `LOCK/UNLOCK TABLES`, `ALTER`, `CREATE`, `DROP`, `RENAME`.
- Use prepared statements such as `PREPARE` and `EXECUTE`.
- Use dynamic SQL statements.

From MySQL version 5.1.4. a trigger can call a stored procedure or stored function, which was a limitation in previous versions.

## Create a trigger in MySQL

In order to create a new trigger, you use the `CREATE TRIGGER` statement. 

```sql
CREATE TRIGGER trigger_name trigger_time trigger_event
ON table_name
FOR EACH ROW
BEGIN
...
END
```

- You put the trigger name after the `CREATE TRIGGER` statement. The trigger name should follow the naming conventions defined previously. 
- You must specify the activation time when you define a trigger. Trigger activation time can be `BEFORE` or `AFTER`. 
- The trigger event can be `INSERT`, `UPDATE`, `DELETE`.
- A trigger must associated with a specific table. Without a table trigger would not exist therefore you have to specify the table name after the `ON` keyword.
- You place the SQL statements between `BEGIN` and `END` block.

```sql
CREATE TABLE employees_audit (
    id INT AUTO_INCREMENT PRIMARY KEY,
    employeeNumber INT NOT NULL,
    lastname VARCHAR(50) NOT NULL,
    changedat DATETIME DEFAULT NULL,
    action VARCHAR(50) DEFAULT NULL
);

DELIMITER $$
CREATE TRIGGER before_employee_update 
    BEFORE UPDATE ON employees
    FOR EACH ROW 
BEGIN
    INSERT INTO employees_audit
    SET action = 'update',
     employeeNumber = OLD.employeeNumber,
        lastname = OLD.lastname,
        changedat = NOW(); 
END$$
DELIMITER ;
```

Inside the body of the trigger we used the `OLD` keyword to access `empoloyeeNumber` and `lastname` column of the row affected by trigger.

Notice that in a trigger defined for INSERT you can use `NEW` keyword only. You cannot use the `OLD` keyword. Howver, in the trigger defined for `DELETE`, there is no new row so you can use the `OLD` keyword only. In the `UPDATE` trigger, `OLD` refers to the row before it is updated and `NEW` refers to the row after it is updated.

Then, to view all triggers in the current database you can use the `SHOW TRIGGERS statement.

```sql
SHOW TRIGGERS;
```

## Create multiple triggers for the same trigger event and action time

Before MySQL version 5.7.2 you can only create one trigger for an event in a table e.g., you can only create one trigger for the `BEFORE UPDATE` or `AFTER UPDATE` event. MySQL 5.7.2+ lifts this limitation and allows you to create multiple triggers for the same event and action time in a table. The triggers will activate sequentially when an event occurs.

The syntax for creating the first trigger remains the same. In case you have multiple triggers for the same event in a table, MySQL will invoke the triggers in the order that they were created. To change the order of the triggers you need to specify `FOLLOWS` or `PRECEDES` after the `FOR EACH ROW` clause.

- The `FOLLOWS` option allows the new trigger to activate after the existing trigger.
- The `PRECEDES` option allows the new trigger to activate before the existing trigger.

The following is the syntax of createing a new additional trigger with explicit order:

```sql
DELIMITER $$
CREATE TRIGGER  trigger_name
[BEFORE|AFTER] [INSERT|UPDATE|DELETE] ON table_name
FOR EACH ROW [FOLLOWS|PRECEDES] existing_trigger_name
BEGIN
…
END$$
DELIMITER ;
```

You can view information on trigger order by using

```sql
SELECT 
    trigger_name, action_order
FROM
    information_schema.triggers
WHERE
    trigger_schema = 'classicmodels'
ORDER BY event_object_table , 
         action_timing , 
         event_manipulation
```

## Managing triggers in MySQL

After creating a trigger, you can display its definition in the data folder, which contains trigger definition file. A trigger is stored as a plain text file in the following data folder:

```
/data_folder/database_name/table_name.trg
```

MySQL provides you with an alternative way to display the trigger by querying the triggers table in the table `information_schema` database as follows:

```sql
SELECT 
    *
FROM
    information_schema.triggers
WHERE
    trigger_schema = 'database_name'
        AND trigger_name = 'trigger_name';
```

The statement allows you to view both content of the tirgger and it's metadata such as associated table name and definer, which is the name of the MySQL user who created the trigger.

If you want to retrieve all triggers in a particular database, you need to query data from the triggers table in the `information_schema` database using the following `SELECT` statement.

```sql
SELECT 
    *
FROM
    information_schema.triggers
WHERE
    trigger_schema = 'database_name';
```

To find all triggers associated with a particular table, you use following query:

```sql
SELECT 
    *
FROM
    information_schema.triggers
WHERE
    trigger_schema = 'database_name'
        AND event_object_table = 'table_name';
```

For example, the following statement returns all triggers associated with the `employees` table in the `classicmodels` database.

```sql
SELECT 
    *
FROM
    information_schema.triggers
WHERE
    trigger_schema = 'classicmodels'
        AND event_object_table = 'employees';
```

Another quick way to diplsay triggers in a particular database is to use `SHOW TRIGGERS` statement as follows:

```sql
SHOW TRIGGERS [FROM|IN] database_name
[LIKE expr | WHERE expr];
```

```sql
SHOW TRIGGERS FROM classicmodels
WHERE `table` = 'employees';
```

MySQL returns the following columns when you execute the `SHOW TRIGGERS` statement.

- Trigger: stores the name of the trigger e.g., before_employee_update trigger.
- Event: specifies the event e.g., INSER, UPDATE, or DELETE that invokes the trigger.
- Table: specifies the tyable where the trigger is associated with e.g. employees table.
- Statement: stores the statement or compound statement that is going to execute when the trigger is invoked.
- Timing: accepts two values - BEFORE and AFTER. It specifies the activation time of the trigger.
- Created: logs the created time when you created the trigger.
- sql_mode: specifies the SQL mode when the trigger executes.
- Definer: logs the account who created the trigger.

Notice that to execute the `SHOW TRIGGER` statement, you must have the `SUPER` privilege.

## Removing trigger

To remove an existing trigger, you use `DROP TRIGGER` statement as follows:

```sql
DROP TRIGGER table_name.trigger_name;
```

```sql
DROP TRIGGER employees.before_employees_update;
```

To modify a trigger, you have to delete it first an recreate it with the new code. There is no such ALTER TRIGGER statement available in MySQL, therefore, you cannot modify an existing trigger like modifying other database objects such as tables, views, and stored procedures.

## Working with MySQL Scheduled Event

A MySQL events is a task that runs based on a predefined schedule therefore sometimes it is referred to as a scheduled event. MySQL event is also known as `temporal trigger` because it is trigger by time, not by table update like a trigger. A MySQL event is similar to a cronjob in UNIX or a task scheduler in Windows.

You can use MySQL events in many cases such as optimizing database tables, cleaning up logs, archiving data, or generate complex reports during off-peak-time.

### MySQL event scheduler configuration

MySQL uses a special thread called event schedule thread to execute all scheduled events. You can see the status of event scheduler thread by executing:

```sql
SHOW PROCESSLIST;
```

By default, the event scheduler thread is not enabled. To enable and start the event scheduler thread, you need to execute the following command:

```sql
SET GLOBAL event_scheduler = ON;
```

## Creating new MySQL events

Creating an event is simar to creating other database objects such as stored procedures or triggers. An event is a named object that contains SQL statements.

A stored procedure is only executed when it is invoked directly; a trigger is executed when an event associated with a table such as an inser, update or delete event occurs while an event can be executed once or more regular intervals.

To create a schedule event, you use the `CREATE EVENT` statement as follows:

```sql
CREATE EVENT [IF NOT EXIST] event_name
ON SCHEDULE schedule
DO event_body
```

You put a schedule after the `ON SCHEDULE` clause. If the event is a one-time event, you use the syntax `AT timestamp [+INTERVAL]`. If the event is a recurring event, you use the `EVERY interval STARTS timestamp [+interval] ENDS timestamp [+INTERVAL]`.

```sql
CREATE EVENT IF NOT EXISTS test_event_01
ON SCHEDULE AT CURRENT_TIMESTAMP
DO
  INSERT INTO messages(message,created_at)
  VALUES('Test MySQL Event 1',NOW());
```

When event is expired, it is automatically dropped. To change the behaviour, you can use `ON COMPLETION PRESERVE` clause. The following statement creates another one-time event that is executed after its creation time 1 minute and not dropped after execution.

```sql
CREATE EVENT test_event_02
ON SCHEDULE AT CURRENT_TIMESTAMP + INTERVAL 1 MINUTE
ON COMPLETION PRESERVE
DO
   INSERT INTO messages(message,created_at)
   VALUES('Test MySQL Event 2',NOW());
```

Recurring events

```sql
CREATE EVENT test_event_03
ON SCHEDULE EVERY 1 MINUTE
STARTS CURRENT_TIMESTAMP
ENDS CURRENT_TIMESTAMP + INTERVAL 1 HOUR
DO
   INSERT INTO messages(message,created_at)
   VALUES('Test MySQL recurring Event',NOW());
```

Drop MySQL Events

```sql
DROP EVENT [IF EXIST] test_event_03;
```

## Modifying MySQL events

MySQL allows you to change various attributes of an existing event. To change existing events, you use the `ALTER EVENT` statement as follows:

```sql
ALTER EVENT event_name
ON SCHEDULE schedule
ON COMPLETION [NOT] PRESERVE
RENAME TO new_event_name
ENABLE | DISABLE
DO
  event_body
```

Notice that the `ALTER EVENT` statement is only applied to an existing event. if you try to modify a nonexistend event, MySQL will issue an error message therefore, you should always use the `SHOW EVENTS` statement to check the event for its existince before changing it.

```sql
SHOW EVENTS FROM classicmodels
```

Changing schedules

```sql
ALTER EVENT test_event_04
ON SCHEDULE EVERY 2 MINUTE
```

Changing event body

```sql
ALTER EVENT test_event_04
DO
   INSERT INTO messages(message,created_at)
   VALUES('Message from event',NOW());
```

Disable events

```sql
ALTER EVENT test_event_04
DISABLE;
```

Enable events

```sql
ALTER EVENT test_event_04
ENABLE;
```

MySQL does not provide you with the `RENAME EVENT` statement. Fortunately, you can use the `ALTER EVENT` to rename an existing event as follows:

```sql
ALTER EVENT test_event_04
RENAME TO test_event_05;
```

Move events to another database

```sql
ALTER EVENT classicmodels.test_event_05
RENAME TO newdb.test_event_05
```