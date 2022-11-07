# Transactions

MySQL transaction allows you to execute a set of MySQL operations to ensure that the database never contains the result of parial operations. In a set of operations, if one of them fails, the rollback occurs to restore the database to it's original state. If no error occurs, the entire set of statements is commited to the database.

### Transaction statements

- To start a transaction you use `START TRANSACTION` statement. The `BEGIN` or `BEGIN WORK` are aliases to it.
- To commit the current transaction and make it' s changes permanent, you use `COMMIT` statement.
- To roll back the current tranaction and cancel it's changes, you use `ROLLBACK` statement.
- To disable or enable the auto-commit mode for the current transaction, you use `SET autocommit`

```sql
SET autocommit = 0;
```

Transaction example:

```sql
-- 1. start a new transaction
START TRANSACTION;
 
-- 2. Get the latest order number
SELECT 
    @orderNumber:=MAX(orderNUmber)+1
FROM
    orders;
 
-- 3. insert a new order for customer 145
INSERT INTO orders(orderNumber,
                   orderDate,
                   requiredDate,
                   shippedDate,
                   status,
                   customerNumber)
VALUES(@orderNumber,
       '2005-05-31',
       '2005-06-10',
       '2005-06-11',
       'In Process',
        145);
        
-- 4. Insert order line items
INSERT INTO orderdetails(orderNumber,
                         productCode,
                         quantityOrdered,
                         priceEach,
                         orderLineNumber)
VALUES(@orderNumber,'S18_1749', 30, '136', 1),
      (@orderNumber,'S18_2248', 50, '55.09', 2); 
      
-- 5. commit changes    
COMMIT;
```

# Table locking

A lock is a flag associated with a table. MySQL allows a client session to explicitly acquire a table lock for  preventing other sessions from accessing the same table during a specific period. A client session can acquire or release table locks only for itself.

```sql
LOCK TABLES table_name [READ | WRITE]
```

To lock a table you specify its name after the `LOCK TABLES` keywords. In addition, you specify the type of lock, either `READ` or `WRITE`.

To release a lock for a table:

```sql
UNLOCK TABLES;
```

### Read locks

- A `READ` lock for a table can be acquired by multiple sessions at the same time. In addition, other sessions can read data from the table without acquiring the lock.
- The session that holds the `READ` lockcan only read data from the table, but cannot write. In addition, other sessions cannot write data to the table until `READ` lock is released. The write operations from another session will be put into the waiting states until the `READ` lock is released.
- If the session is terminated, either normally or abnormally, MySQL will release all the locks implicitly. 

### Write locks

- The only session that holds the lock of a table can read and write data from the table.
- Other sessions cannot read data from and write data to the table until the `WRITE` lock is released.