# MySQL administration

## Getting started with MySQL Access Control system

MySQL implements a sophisticated access control and privilege system that allows you to create comprehensive access rules for handling client operations and effectively preventing unauthorized clients from accessing the database system.

The MySQL access control has two stages when a client connects to the server:
- Connection verification: aclient, which connects to the MySQL database server, needs to have a valid username and password. In addition, the host from which the client connects has to match the host in the MySQL grant table.
- Request verification: once a connection is established successfully, for each statement issued by the client, MySQL checks whether the client has sufficient privileges to execute that particular statement. mySQL has the ability to check a privilege at the database, table, and field levels.

There is a datbase named `mysql` created automatically by MySQL installer. The `mysql` database contains five main grant tables. You often manipulate these tables indirectly through the statements such as `GRAND` and `REVOKE`.
- `user` - contains user account and global privilege columns. MySQL uses the `user` table to either accept or reject a connection from a host. A privilege granted in the `user` table is effective to all databases on the MySQL server.
- `db` - contains database level privileges. MySQL uses the `db` table to determine which database a user can access and from which host. A privilege granted a the database level in the `db` table applies to the database and all objects belong to that database e.g. tables, triggers, views, stored procedures etc.
- `table_priv` and `columns_priv` - contains table-level and column-level privileges. A privilege granted in the `table_priv` table applies to the table and it's columns while a privilege granted in `columns_priv` table applies only to a specific column of a table.
`procs_priv` contains stored functions and stored procedures privileges.

MySQL makes use of these tables to control the privileges of MySQL database server. Understanding tables is very important before you can implement you own flexible access control system.

## Create user accounts using CREATE USER statement

In MySQL , you can specify not only who can connect to the database server but also from which host that the user connects. Therefore, a user account in MySQL consists of a username and a host name separated by the `@` character.

For example, if the `admin` user connects to the MySQL database server from `localhost`, the user account is `admin@localhost`.

The `admin` user only can connect to the MySQL database server from the `localhost`, not from a remote host. This makes the MySQL database server even more secure.

In addition, by combining the username and host, it is possible to setup multiple accounts with the same name but can connect from different hosts with different privileges.

MySQL stored the user accounts in the `user` grants table of the `mysql` database.

### Creating user accounts using MySQL CREATE USER statement

MySQL provides `CREATE USER` statement that allows you to create a new user account. The syntax of the `CREATE USER` statement is as follows:

```sql
CREATE USER user_account IDENTIFIED BY password;
```

The `user_acount` in the format `'username'@'hostname'` is followed by the `CREATE USER` clause.

The password is specified in the `IDENTIFIED BY` clause. The password must be in clear text. MySQL will encrypt the password before saving the user account into the `user` table.

```sql
CREATE USER dbadmin@localhost 
IDENTIFIED BY 'secret';
```

To view the privileges of a user account, you use the `SHOW GRANTS` statements as follows:

```sql
SHOW GRANTS FOR dbadmin@localhost;
```

```
+---------------------------------------------+
| Grants for dbadmin@localhost                |
+---------------------------------------------+
| GRANT USAGE ON *.* TO `dbadmin`@`localhost` |
+---------------------------------------------+
1 row in set (0.00 sec)
```

The *.* n the result shows that the `dbadmin` user account can only login to the database server and has no other privileges. To grant permission to the user, you use the `GRANT` statement.

Note that the part before the dot represents the database and the dot represents the table.

To allow a user to connect from any host, you use the percent (%) wildcard as shown in the example:

```sql
CREATE USER superadmin@'%'
IDENTIFIED BY 'secret';
```

The percent wildcard has the same effect as it is used in the `LIKE` operator, e.g., to allow `mysqladmin` user account to connect to the database server from any subdomain of the `mysqltutorial.org` host, you use the percent wildcard `%` as follows:

```sql
CREATE USER mysqladmin@'%.mysqltutorial.org'
IDENTIFIED by 'secret';
```

You can also use the underscode wilcard `_`.
If you omit the `hostname` part of the user account, MySQL will accept it and allow the user to connect from any host.

## Change user password

### Using UPDATE statement

The first way to change the password is to use the `UPDATE` statement to update the `user` table of the `mysql` database. After executing the `UPDATE` statement, you also need to execute the `FLUSH PRIVILEGES` statement to reload privileges from the grant table in the `mysql` database.

```sql
USE mysql;
 
UPDATE user 
SET password = PASSWORD('dolphin')
WHERE user = 'dbadmin' AND 
      host = 'localhost';
 
FLUSH PRIVILEGES;
```

Note that from MySQL 5.7.6, the user table uses the `authentication_string` column only to store the password. In addition, it removed the password column.

Therefore if you use MySQL 5.7.6+, you must use the `authentication_string` column in the `UPDATE` statement instead:

```sql
USE mysql;
 
UPDATE user 
SET authentication_string = PASSWORD('dolphin')
WHERE user = 'dbadmin' AND 
      host = 'localhost';
 
FLUSH PRIVILEGES;
```

Notice that the `PASSWORD()` function computes the hash value from plain text.

### Change user password using the SET PASSWORD

```sql
SET PASSWORD FOR 'dbadmin'@'localhost' = PASSWORD('bigshark');
```

From version 5.7.6, MySQL deprecated this syintax and may remove it in the future releases. Instead, it uses the plaintet password as follows:

```sql
SET PASSWORD FOR 'dbadmin'@'localhost' = bigshark;
```

### Change mysql user password using ALTER USER

```sql
ALTER USER dbadmin@localhost IDENTIFIED BY 'lit
```

In case you want to reset the password of the MySQL `root` account, you need to force the MySQL database server to stop and restart without using grant table validation.

## Use GRANT statement to grant privileges to a user

After creating a new user account, the user doesnt have any privileges. To grant privileges to a user account, you use the `GRANT` statement:

```sql
GRANT privilege,[privilege],.. ON privilege_level 
TO user [IDENTIFIED BY password]
[REQUIRE tsl_option]
[WITH [GRANT_OPTION | resource_option]];
```

- First, specify one or more privileges after the `GRANT` keyword. If you grant the user multiple privileges, each privilege is separated by a comma.
- Next, specify the `privilege_level` that determines the level at which the privileges apply. MySQL supports global (`*.*`), database (`database.*`), table (`database.table`) and columns levels. If you use column privilege level, you must specify one or a list of comma-separated column after each privilege.
- Then, place the user that you want to grant privileges. If user already exists, the `GRANT` statement modifies its privilege. Otherwise, the `GRANT` statement creates a new user. The optional clause `IDENTIFIED BY` allows you set a new password for the user.
- After that, you specify whether the user has to connect to the database server over a secure connection such as SSL, X059, etc.
- Finally, the optional `WITH GRANT` option clause allows you to grant other users or remove from other users the privileges that you possess. In addition, you can use the `WITH` clause to allocate MySQL database server's resource e.g., to set how many connections or statements that the user can use per hour. This is very helpful in the shared environments such as MySQL shared hosting.

Notice that in order to use the `GRANT` statement, you must have the `GRANT OPTION` privilege and the privileges that you are granting. If the `read_only` system variable is enabled, you need to have the `SUPER` privilege to execute the `GRANT` statement.

```sql
CREATE USER super@localhost IDENTIFIED BY 'dolphin';
GRANT ALL ON *.* TO 'super'@'localhost' WITH GRANT OPTION;
```

```sql
CREATE USER auditor@localhost IDENTIFIED BY 'whale';
GRANT ALL ON classicmodels.* TO auditor@localhost;
```

```sql
CREATE USER rfc IDENTIFIED BY 'shark';
GRANT SELECT, UPDATE, DELETE ON classicmodels.* TO rfc;
```

The following table illustrates all permissible privileges that you can use the `GRANT` and `REVOKE` statement:

<table summary="Permissible Privileges for GRANT and REVOKE"><tbody><tr><td style="text-align: center;" rowspan="2"><strong>Privilege</strong></td><td style="text-align: center;" rowspan="2"><strong>Meaning</strong></td><td style="text-align: center;" colspan="6"><strong>Level</strong></td></tr><tr><td><strong>Global</strong></td><td><strong>Database</strong></td><td><strong>Table</strong></td><td><strong>Column</strong></td><td><strong>Procedure</strong></td><td><strong>Proxy</strong></td></tr><tr><td>ALL [PRIVILEGES]</td><td>Grant all privileges at specified access level except GRANT OPTION</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>ALTER</td><td style="text-align: center;">Allow user to use of ALTER TABLE statement</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>ALTER ROUTINE</td><td>Allow user to alter or drop stored routine</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;">X</td><td style="text-align: center;"></td></tr><tr><td>CREATE</td><td>Allow user to create database and table</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>CREATE ROUTINE</td><td>Allow user to create stored routine</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>CREATE TABLESPACE</td><td>Allow user to create, alter or drop tablespaces and log file groups</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>CREATE TEMPORARY TABLES</td><td>Allow user to create temporary table by using CREATE TEMPORARY TABLE</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>CREATE USER</td><td>Allow user to use the CREATE USER, DROP USER, RENAME USER, and REVOKE ALL PRIVILEGES statements.</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>CREATE VIEW</td><td>Allow user to create or modify view.</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>DELETE</td><td>Allow user to use DELETE</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>DROP</td><td>Allow user to drop database, table and view</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>EVENT</td><td>Enable use of events for the Event Scheduler.</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>EXECUTE</td><td>Allow user to execute stored routines</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>FILE</td><td>Allow user to read any file in the database directory.</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>GRANT OPTION</td><td>Allow user to have privileges to grant or revoke privileges from other accounts.</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;">X</td><td style="text-align: center;">X</td></tr><tr><td>INDEX</td><td>Allow user to create or remove indexes.</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>INSERT</td><td>Allow user to use INSERT statement</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>LOCK TABLES</td><td>Allow user to use LOCK TABLES on tables for which you have the SELECT privilege</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>PROCESS</td><td>Allow user to see all processes with SHOW PROCESSLIST statement.</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>PROXY</td><td>Enable user proxying.</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>REFERENCES</td><td>Allow user to create foreign key</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>RELOAD</td><td>Allow user to use FLUSH operations</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>REPLICATION CLIENT</td><td>Allow user to query to see where master or slave servers are</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>REPLICATION SLAVE</td><td>Allow the user to use replicate slaves to read binary log events from the master.</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>SELECT</td><td>Allow user to use SELECT statement</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>SHOW DATABASES</td><td>Allow user to show all databases</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>SHOW VIEW</td><td>Allow user to use SHOW CREATE VIEW statement</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>SHUTDOWN</td><td>Allow user to use mysqladmin shutdown command</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>SUPER</td><td>Allow user to use other administrative operations such as CHANGE MASTER TO, KILL, PURGE BINARY LOGS, SET GLOBAL, and mysqladmin command</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>TRIGGER</td><td>Allow user to use TRIGGER operations.</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>UPDATE</td><td>Allow user to use UPDATE statement</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;">X</td><td style="text-align: center;"></td><td style="text-align: center;"></td></tr><tr><td>USAGE</td><td>Equivalent to “no privileges”</td><td></td><td></td><td></td><td></td><td></td><td></td></tr></tbody></table>

## Revoking privileges from users using MySQL REVOKE

```sql
REVOKE   privilege_type [(column_list)]      
        [, priv_type [(column_list)]]...
ON [object_type] privilege_level
FROM user [, user]..
```

Revoke all privileges from a user

```sql
REVOKE ALL PRIVILEGES, GRANT OPTION FROM user [, user]…
```

Revoke proxy user

```sql
REVOKE PROXY ON user FROM user [, user]...
```

View grants

```sql
SHOW GRANTS FOR user;
```

```sql
CREATE USER IF EXISTS rfc IDENTIFIED BY 'dolphin';
GRANT SELECT, UPDATE, DELETE ON  classicmodels.* TO rfc;
REVOKE UPDATE, DELETE ON classicmodels.*  FROM rfc;
```

## MySQL Roles

Typically, you have a number of users with the same set of privileges. Previously the only way to grant and revoke privileges to multiple users is to change privileges of each user individually, which is time-consuming.

To make it easier, MySQL provided a new object called role that is named collection of privileges. 

If you want to grant the same set of privileges to multiple users you should do as follows:
1. Create a new role
2. Grant privileges to the role
3. Grant the role to the users

In case you want to change the privileges of the users, you need to change the privileges of the granted role only. The changes will take effect to all users to which the role granted.

```sql
CREATE ROLE crm_dev, crm_read, crm_write;
GRANT ALL ON crm.* TO crm_dev;
GRANT SELECT ON crm.* TO crm_read;
GRANT INSERT, UPDATE, DELETE ON crm.* TO crm_write;

-- developer user 
CREATE USER crm_dev1@localhost IDENTIFIED BY 'Secure$1782';
-- read access user
CREATE USER crm_read1@localhost IDENTIFIED BY 'Secure$5432';    
-- read/write users
CREATE USER crm_write1@localhost IDENTIFIED BY 'Secure$9075';   
CREATE USER crm_write2@localhost IDENTIFIED BY 'Secure$3452';

GRANT crm_dev TO crm_dev1@localhost; 
GRANT crm_read TO crm_read1@localhost;
GRANT crm_read, crm_write TO crm_write1@localhost, crm_write2@localhost;
```

Set default role

```sql
SET DEFAULT ROLE ALL TO crm_read1@localhost;
```

```sql
REVOKE INSERT, UPDATE, DELETE ON crm.* FROM crm_write;
```

```sql
GRANT INSERT, UPDATE, DELETE ON crm.* FOR crm_write;
```

```sql
DROP ROLE role_name, role_name, ...;
```

```sql
DROP ROLE crm_read, crm_write;
```

Copy privileges from one user to another

```sql
GRANT crm_dev1@localhost TO crm_dev2@localhost;
```

### Setting active roles

A user account can modify the current user's effective privileges within the current session by specifying which granted role is active.

The following statement set the active role to `NONE`, meaning no active role.

```sql
SET ROLE NONE;
```

To set active roles to all granted role, you use:

```sql
SET ROLE ALL;
```

To set active roles to default roles that set by the `SET DEFAULT ROLE` statement, you use:

```sql
SET ROLE DEFAULT;
```

To set active named roles you use:

```sql
SET ROLE granted_role_1, granted_role_2;
````

## Remove user accounts using DROP USER statement

```sql
DROP USER dbadmin@mysqltutorial.org;
```

If the user has an active session, you should kill the session before using `DROP USER`.
It can be done by finding the process id with `SHOW PROCESSLIST` and using the `KILL` command.

## Maintaining MySQL database tables

MySQL provides several useful statements that allow you to maintain database tables effectively. Those statements enable you to analyze, optimize, check and repair database tables.

### Analyze table statement

MySQL query optimizer is an important component of the MySQL server that creates an optimal query execution plan for a query. For a particular query, the query optimizer uses the stored key distribution and other factors to decide the order in which tables should be joined when you performing the join, and which index should be used for a specific table.

However, the key distributions can be sometimes inaccurate e.g., after you have done a lot of data changes in the table including insert, delete or update. If the key distribution is not accurate, the query optimizer may pick a bad query execution plan that may cause a severe performance issue.

To solve this problem you can run the `ANALYZE TABLE` statement for the table e.g., the following stateement analyzes the payments table:

```sql
ANALYZE TABLE payments;
```

If there is no change to the table since the ANALYZE TABLE statement ran, MySQL will not analyze the table again. If you run the statement again, it will say it is already up to date.

### Optimize table statement

While working with the database, you do a log of changes surch as inser, update and delete data in the table that may cause the physical storage of the table fragmented. As a result the performance of database server is degraded.

MySQL provides you wih a statement that allows you to optimize the table to avoid this defragmenting problem. The following illustrates how to optimize a table:

```sql
OPTIMIZE TABLE table_name;
```

It is recommended that you execute this statement for the tables that are updated frequently. 

### Check table statement

Something wrong can happen to the database server e.g., the server was shut down unexpectedly, error while writing data to the hard disk, etc. These situations could make the database operate incorrectly and in the worst case, it can be crashed.

MySQL allows you to check the integrity of database tables by using the `CHECK TABLE` statement. The following illustrates the syntax of the `CHECK TABLE` statement:

```sql
CHECK TABLE table_name;
```

The `CHECK TABLE` statement checks both table and its indexes.  This statement only detects problems in a database table but it does not repair them. To repair the table, you use `REPAIR TABLE` statement.

## Repair table statement

The `REPAIR TABLE` statement allows you to repair some errors occurred in database tables. MySQL does not guarantee that the `REPAIR TABLE` statement can repair all errors that the tables may have.

```sql
REPAIR TABLE table_name
```

## Backup databases using mysqldump tool

```sql
mysqldump -u [username] –p[password] [database_name] > [dump_file.sql]
```

Backup structure only

```sql
mysqldump -u [username] –p[password] –no-data [database_name] > [dump_file.sql]
```

Backup multiple databases into a single file

```sql
mysqldump -u [username] –p[password]  [dbname1,dbname2,…] > [dump_file.sql]
mysqldump -u [username] –p[password] –all-database > [dump_file.sql]
```

## Show databases: list all databases in MySQL

```sql
mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| classicmodels      |
| information_schema |
| mysql              |
| performance_schema |
| sys                |
| test               |
+--------------------+
6 rows in set (0.00 sec)
```

```sql
SHOW DATABASES LIKE '%schema';
+--------------------+
| Database (%schema) |
+--------------------+
| information_schema |
| performance_schema |
+--------------------+
2 rows in set (0.00 sec)
```

```sql
SELECT schema_name
FROM information_schema.schemata
WHERE schema_name LIKE '%schema' OR 
      schema_name LIKE '%s';

+--------------------+
| SCHEMA_NAME        |
+--------------------+
| information_schema |
| performance_schema |
| sys                |
| classicmodels      |
+--------------------+
4 rows in set (0.00 sec)
```

## Show tables: List tables in database

```sql
+--------------------+
| SCHEMA_NAME        |
+--------------------+
| information_schema |
| performance_schema |
| sys                |
| classicmodels      |
+--------------------+
4 rows in set (0.00 sec)
```

Include table type (base table or view)

```sql
> SHOW FULL TABLES
+-------------------------+------------+
| Tables_in_classicmodels | Table_type |
+-------------------------+------------+
| contacts                | VIEW       |
| customers               | BASE TABLE |
| employees               | BASE TABLE |
| offices                 | BASE TABLE |
| orderdetails            | BASE TABLE |
| orders                  | BASE TABLE |
| payments                | BASE TABLE |
| productlines            | BASE TABLE |
| products                | BASE TABLE |
+-------------------------+------------+
9 rows in set (0.00 sec)
```

```sql
> SHOW TABLES LIKE 'p%';
+------------------------------+
| Tables_in_classicmodels (p%) |
+------------------------------+
| payments                     |
| productlines                 |
| products                     |
+------------------------------+
3 rows in set (0.00 sec)
```

```sql
> SHOW FULL TABLES WHERE table_type = 'VIEW';
+-------------------------+------------+
| Tables_in_classicmodels | Table_type |
+-------------------------+------------+
| contacts                | VIEW       |
+-------------------------+------------+
1 row in set (0.00 sec)
```

## Show columns and describe

```sql
mysql> DESCRIBE orders;
+----------------+-------------+------+-----+---------+-------+
| Field          | Type        | Null | Key | Default | Extra |
+----------------+-------------+------+-----+---------+-------+
| orderNumber    | int(11)     | NO   | PRI | NULL    |       |
| orderDate      | date        | NO   |     | NULL    |       |
| requiredDate   | date        | NO   |     | NULL    |       |
| shippedDate    | date        | YES  |     | NULL    |       |
| status         | varchar(15) | NO   |     | NULL    |       |
| comments       | text        | YES  |     | NULL    |       |
| customerNumber | int(11)     | NO   | MUL | NULL    |       |
+----------------+-------------+------+-----+---------+-------+
7 rows in set (0.01 sec)
```

```sql
SHOW COLUMNS FROM table_name;
SHOW COLUMNS FROM database_name.table_name;
SHOW COLUMNS FROM table_name IN database_name;
SHOW FULL COLUMNS FROM table_name;
```

```sql
mysql> SHOW FULL COLUMNS FROM payments \G;
*************************** 1. row ***************************
     Field: customerNumber
      Type: int(11)
 Collation: NULL
      Null: NO
       Key: PRI
   Default: NULL
     Extra:
Privileges: select,insert,update,references
   Comment:
*************************** 2. row ***************************
     Field: checkNumber
      Type: varchar(50)
 Collation: latin1_swedish_ci
      Null: NO
       Key: PRI
   Default: NULL
     Extra:
Privileges: select,insert,update,references
   Comment:
*************************** 3. row ***************************
     Field: paymentDate
      Type: date
 Collation: NULL
      Null: NO
       Key:
   Default: NULL
     Extra:
Privileges: select,insert,update,references
   Comment:
*************************** 4. row ***************************
     Field: amount
      Type: decimal(10,2)
 Collation: NULL
      Null: NO
       Key:
   Default: NULL
     Extra:
Privileges: select,insert,update,references
   Comment:
4 rows in set (0.01 sec)
```

```sql
mysql> SHOW COLUMNS FROM payments LIKE 'c%';
+----------------+-------------+------+-----+---------+-------+
| Field          | Type        | Null | Key | Default | Extra |
+----------------+-------------+------+-----+---------+-------+
| customerNumber | int(11)     | NO   | PRI | NULL    |       |
| checkNumber    | varchar(50) | NO   | PRI | NULL    |       |
+----------------+-------------+------+-----+---------+-------+
2 rows in set (0.01 sec)
```

## List all users in server

```sql
SELECT user from mysql.user
```

Describe user

```sql 
DESC user;
```

Show current user

```sql
mysql> SELECT user();
+-----------------+
| user()          |
+-----------------+
| local@localhost |
+-----------------+
1 row in set (0.00 sec)
```

```sql
mysql> SELECT current_user();
+----------------+
| current_user() |
+----------------+
| local@localhost |
+----------------+
1 row in set (0.00 sec)
```

Show current logged users

```sql
SELECT 
    user, 
    host, 
    db, 
    command 
FROM 
    information_schema.processlist;
 
+-------+-----------------+---------------+---------+
| user  | host            | db            | command |
+-------+-----------------+---------------+---------+
| local | localhost:50591 | classicmodels | Sleep   |
| root  | localhost:50557 | NULL          | Query   |
+-------+-----------------+---------------+---------+
2 rows in set (0.00 sec)
```

## Show processlist

Sometimes you may get "too many connections" error returned by the server. To find out the reasons you can use `SHOW PROCESSLIST` command and use the `KILL` statement to kill the idle threads.

```sql
SHOW [FULL] PROCESSLIST;
```

```sql
mysql>SHOW PROCESSLIST;
 
+----+-----------------+-----------------+---------------+---------+------+------------------------+------------------+
| Id | User            | Host            | db            | Command | Time | State                  | Info             |
+----+-----------------+-----------------+---------------+---------+------+------------------------+------------------+
|  4 | event_scheduler | localhost       | NULL          | Daemon  | 2246 | Waiting on empty queue | NULL             |
| 14 | root            | localhost:50924 | NULL          | Query   |    0 | starting               | SHOW PROCESSLIST |
| 15 | car             | localhost:50933 | classicmodels | Sleep   |    2 |                        | NULL             |
+----+-----------------+-----------------+---------------+---------+------+------------------------+------------------+
3 rows in set (0.00 sec)
```

- `id` - the client process id
- `usder` - the username associated with the thread
- `host` - the host to which the client is connected
- `db` - the default database if one selected otherwise `NULL`.
- `command` - the command type
- `time` - the number of seconds that the current thread has been in its current state
- `state` - the thread state which represents an action, event, or state that indicates what thread is executing.
- `info` the statement is executed, or `NULL` if it is not executing any statement. If you do not use the `FULL` keyword in the `SHOW PROCESSLIST` command, then only the first 100 characters of each statement are returned in the info column.