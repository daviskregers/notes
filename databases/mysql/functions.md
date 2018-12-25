# MySQL functions

## Aggregate functions

The data that you need is not always directly stored in the datables. However, you can get it by performing the calculations of the stored data when you select it.

For example, you cannot get the total amount of each order by simply querying from the orderdetails table bcause the orderdetails table stores only quentity and price of each item, you have to select the quentity and price of an item for each order and calculate the order's total.

To perform such caulculations in a query, you use aggregate functions.

By definition, an aggregate function performs a calculation on a set of values and returns a signle value.

MySQL provides many aggregate functions that include `AVG`, `COUNT`, `SUM`, `MIN`, `MAX`  etc. An aggregate function ignores NULL values when it performs calculation except for the `COUNT` function.

### AVG function 

The AVG function calculates the average value of a set of values. It ignores NULL values in the calculation. 

```sql
SELECT AVG(buyPrice) average_buy_price
FROM products
```

You use the DISTINCT operator in the AVG function to calculate the average value of the distinct values. For example, if you have a set of values 1,1,2,3, the AVG function with DISTINCT operator will return two i.e., (1 + 2 + 3) / 2.

We often use the AVG() function in conjunction with the GROUP BY clause to calculate the average value for each group of rows in a table.

For example, to calculate the average buy price of products for each product line, you use the AVG() function with the GROUP BY clause as the following query:

### COUNT function

The COUNT function returns the number of the rows in a table. 

```sql
SELECT COUNT(*) AS Total
FROM products
```

The COUNT function has several forms such as `COUNT(*) ` and `COUNT(DISTINCT expression)`.

### SUM function 

The SUM function returns the sum of a set of values. The SUM function ignores NULL values. If no matching row found, the SUM function returns a NULL value.

```sql
SELECT productCode,sum(priceEach * quantityOrdered) total
FROM orderdetails
GROUP by productCode
```

### MAX function

The MAX function returns the maximum value in a set of values.

```sql
SELECT MAX(buyPrice) highest_price,
FROM Products
```

### MIN function

The MIN function returns the minimum value in a set of values.

```sql
SELECT MIN(buyPrice) lowest_price,
FROM Products
```

### INSTR function

Sometimes, you want to locate a substring in a string or to check if a substring exists in a string. In this case, you can use a string built-in function called INSTR.

The INSTR function returns the position of the first occurrence of a substring in a string. If the substring is not found in the str, the INSTR function returns zero (0).

The INSTR function accepts two arguments:

- The str is the string that you want to search in.
- The substr is the substring that you want to search for.

The INSTR function is not case sensitive. It means that it does not matter if you pass the lowercase, uppercase, title case, etc., the results are always the same.

If you want the INSTR function to perform searches in case-sensitive manner on a non-binary string, you use the BINARY operator to cast a one the argument of the INSTR function from a non-binary string to a binary string.

```sql
SELECT INSTR('MySQL INSTR', 'MySQL');
SELECT INSTR('MySQL INSTR', 'mysql');
SELECT INSTR('MySQL INSTR', BINARY 'mysql');
```

```sql
SELECT 
    productName
FROM
    products
WHERE
    INSTR(productname,'Car') > 0;
```

### GROUP_CONCAT function

The MySQL GROUP_CONCAT function concatenates strings from a group into a single string with various options.

```sql
SELECT 
    GROUP_CONCAT(country)
FROM
    customers;
```

```sql
SELECT 
    GROUP_CONCAT(DISTINCT country
        ORDER BY country
        SEPARATOR ';')
FROM
    customers;
```

### Standard deviation function

To calculate population starndard deviation, you use one of following functions:

- STD(expression) - returns population standard deviation ofthe expression. the STD function returns NULL if there was no matching row.
- STDDEV(expression) - is equivalent to the STD function. It is provided to be compatible with Oracle database only.
- STDEV_POP - is equivalent to the STD function.

To calculate the sample standard deviation, you use the `STDDEV_SAMP` function.

MySQL also provides some functions for population vaiance and sample variance calculation

- VAR_POP - calculate the population standard variance of the expression
- VARIANCE - equivalent to VAR_POP
- VAR_SAMP - calculates the sample standard variance of the expression

```sql
SELECT FORMAT(STD(orderCount),2)
FROM (SELECT customerNumber, count(*) orderCount
FROM orders
GROUP BY customerNumber) t;
```

## String functions

### CONCAT function

To concatenate two or more quoted string values, you place the string next to each other as the following syntax:


```sql
SELECT 
    concat(contactFirstName,' ',contactLastName) Fullname
FROM
    customers;
```

### LENGTH & CHAR_LENGTH

To get the length of a string measured in bytes, you use the LENGTH  function as follows:
You use the CHAR_LENGTH  function to get the length of a string measured in characters as follows:

```sql
SET @s = CONVERT('MySQL String Length' USING ucs2);
SELECT CHAR_LENGTH(@s), LENGTH(@s);
```

### LEFT

The LEFT function is a string function that returns the left part of a string with a specified length.

```sql
SELECT LEFT('MySQL LEFT', 5);
```

Will return `MySQL`

### REPLACE

MySQL provides you with a useful string function called REPLACE that allows you to replace a string in a column of a table by a new string.

```sql
UPDATE tbl_name 
SET 
    field_name = REPLACE(field_name,
        string_to_find,
        string_to_replace)
WHERE
    conditions;
```

### SUBSTRING

The SUBSTRING function returns a substring with a given length from a string starting at a specific position. MySQL provides various forms of the substring function.

For example, to get the ” SUBSTRING” out of the ” MySQL SUBSTRING” string, the position of the substring must be 7 as the following SELECT statement:

```sql
SELECT SUBSTRING('MYSQL SUBSTRING', 7);
```

### TRIM

MySQL provides a very useful string function named TRIM to help you clean up the data. The following illustrates the syntax of the TRIM function.

MySQL provides a very useful string function named TRIM to help you clean up the data. The following illustrates the syntax of the TRIM function.

```sql
SELECT TRIM(' MySQL TRIM Function ');
```

### FIND_IN_SET

MySQL provides a built-in string function called FIND_IN_SET that allows you to find the position of a string within a comma-separated list of strings.

```sql
SELECT FIND_IN_SET('y','x,y,z'); -- 2
```

### FORMAT

If the result of the expression is a decimal with many decimal places, you can format those numbers, you use the FORMAT function with the following syntax:

```sql
SELECT FORMAT(12500.2015, 2,'de_DE');
```

```sql
SELECT 
    productname,
    CONCAT('$',
            FORMAT(quantityInStock * buyPrice, 2)) stock_value
FROM
    products;
```

## Control flow functions

### CASE

MySQL CASE expression is a flow control structure that allows you to construct conditions inside a query such as SELECT or WHERE clause. MySQL provides you with two forms of the CASE expressions.

```sql
CASE value
WHEN compare_value_1 THEN result_1
WHEN compare_value_2 THEN result_2
…
ELSE result END
```

### IF

The MySQL IF statement allows you to execute a set of SQL statements based on a certain condition or value of an expression. To form an expression in MySQL, you can combine literals, variables, operators, and even functions. An expression can return TRUE FALSE, or NULL.

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

### IFNULL

MySQL IFNULL function is one of the MySQL control flow functions that accepts two arguments and returns the first argument if it is not NULL. Otherwise, the IFNULL function returns the second argument.

```sql
SELECT IFNULL(NULL,'IFNULL function'); -- returns IFNULL function
```

### NULLIF

The NULLIF function is one of the control flow functions that accepts 2 arguments. The NULLIF function returns NULL if the first argument is equal to the second argument, otherwise it returns the first argument.

```sql
SELECT NULLIF(1,1); -- return NULL
SELECT NULLIF(1,2); -- return 1
SELECT NULLIF('MySQL NULLIF','MySQL NULLIF'); -- return NULL
SELECT NULLIF('MySQL NULLIF','MySQL IFNULL'); -- return MySQL NULLIF
SELECT NULLIF(1,NULL); -- return 1 because 1 <=> NULL
SELECT NULLIF(NULL,1); -- return NULL the first argument
```

## Date and time functions

### CURDATE

The CURDATE() function returns the current date as a value in the 'YYYY-MM-DD' format if it is used in a string context or YYYMMDD format if it is used in a numeric context.

```sql
mysql> SELECT CURDATE();
+------------+
| CURDATE()  |
+------------+
| 2017-07-13 |
+------------+
1 row in set (0.00 sec)
```

### DATEDIFF

The MySQL DATEDIFF function calculates the number of days between two  DATE,  DATETIME, or  TIMESTAMP values.

```sql
SELECT DATEDIFF('2011-08-17','2011-08-17'); --  0 day
SELECT DATEDIFF('2011-08-17','2011-08-08'); --  9 days
SELECT DATEDIFF('2011-08-08','2011-08-17'); -- -9 days
```

### DAY

The DAY function returns the day of the month of a given date. The following shows the syntax of the DAY function:

```sql
mysql> SELECT DAY('2010-01-15');
+-------------------+
| DAY('2010-01-15') |
+-------------------+
|                15 |
+-------------------+
1 row in set (0.00 sec)
```

To get the number of days in a month based on a specified date, you combine the LAST_DAY and DAY functions as shown in the following example:

```sql
mysql> SELECT DAY(LAST_DAY('2016-02-03'));
+-----------------------------+
| DAY(LAST_DAY('2016-02-03')) |
+-----------------------------+
|                          29 |
+-----------------------------+
1 row in set (0.00 sec)
```

### DATE_ADD

The DATE_ADD function adds an interval to a DATE or DATETIME value. The following illustrates the syntax of the DATE_ADD function:

```sql
SELECT 
    DATE_ADD('1999-12-31 23:59:59',
        INTERVAL 1 SECOND) result;
 
+---------------------+
| result              |
+---------------------+
| 2000-01-01 00:00:00 |
+---------------------+
1 row in set (0.00 sec)
```

### DATE_SUB

The DATE_SUB() function subtracts a time value (or an interval) from a DATE or DATETIME value. The following illustrates the DATE_SUB() function:

```sql
SELECT DATE_SUB('2017-07-04',INTERVAL 1 DAY) result;
+------------+
| result     |
+------------+
| 2017-07-03 |
+------------+
1 row in set (0.00 sec) 
```

### DATE_FORMAT

To format a date value to a specific format, you use the DATE_FORMAT function. The syntax of the DATE_FORMAT function is as follows:

```sql
SELECT 
    orderNumber,
    DATE_FORMAT(orderdate, '%Y-%m-%d') orderDate,
    DATE_FORMAT(requireddate, '%a %D %b %Y') requireddate,
    DATE_FORMAT(shippedDate, '%W %D %M %Y') shippedDate
FROM
    orders;
```

<table><thead><tr><th>Specifier</th><th>Meaning</th></tr></thead><tbody><tr><td>%a</td><td>Three-characters abbreviated weekday name e.g., Mon, Tue, Wed, etc.</td></tr><tr><td>%b</td><td>Three-characters abbreviated month name e.g., Jan, Feb, Mar, etc.</td></tr><tr><td>%c</td><td>Month in numeric e.g., 1, 2, 3…12</td></tr><tr><td>%D</td><td>Day of the month with English suffix e.g., 0th, 1st, 2nd, etc.</td></tr><tr><td>%d</td><td>Day of the month with leading zero if it is 1 number e.g., 00, 01,02, …31</td></tr><tr><td>%e</td><td>Day of the month without leading zero e.g., 1,2,…31</td></tr><tr><td>%f</td><td>Microseconds in the range of 000000..999999</td></tr><tr><td>%H</td><td>Hour in 24-hour format with leading zero e.g., 00..23</td></tr><tr><td>%h</td><td>Hour in 12-hour format with leading zero e.g., 01, 02…12</td></tr><tr><td>%I</td><td>Same as %h</td></tr><tr><td>%i</td><td>Minutes with leading zero e.g., 00, 01,…59</td></tr><tr><td>%j</td><td>Day of year with leading zero e.g., 001,002,…366</td></tr><tr><td>%k</td><td>Hour in 24-hour format without leading zero e.g., 0,1,2…23</td></tr><tr><td>%l</td><td>Hour in 12-hour format without leading zero e.g., 1,2…12</td></tr><tr><td>%M</td><td>Full month name e.g., January, February,…December</td></tr><tr><td>%m</td><td>Month name with leading zero e.g., 00,01,02,…12</td></tr><tr><td>%p</td><td>AM or PM, depending on other time specifiers</td></tr><tr><td>%r</td><td>Time in 12-hour format hh:mm:ss AM or PM</td></tr><tr><td>%S</td><td>Seconds with leading zero 00,01,…59</td></tr><tr><td>%s</td><td>Same as %S</td></tr><tr><td>%T</td><td>Time in 24-hour format hh:mm:ss</td></tr><tr><td>%U</td><td>Week number with leading zero when the first day of week is Sunday e.g., 00,01,02…53</td></tr><tr><td>%u</td><td>Week number with leading zero when the first day of week is Monday e.g., 00,01,02…53</td></tr><tr><td>%V</td><td>Same as %U; it is used with %X</td></tr><tr><td>%v</td><td>Same as %u; it is used with %x</td></tr><tr><td>%W</td><td>Full name of weekday e.g., Sunday, Monday,…, Saturday</td></tr><tr><td>%w</td><td>Weekday in number (0=Sunday, 1= Monday,etc.)</td></tr><tr><td>%X</td><td>Year for the week in four digits where the first day of the week is Sunday; often used with %V</td></tr><tr><td>%x</td><td>Year for the week, where the first day of the week is Monday, four digits; used with %v</td></tr><tr><td>%Y</td><td>Four digits year e.g., 2000 and 2001.</td></tr><tr><td>%y</td><td>Two digits year e.g., 10,11,and 12.</td></tr><tr><td>%%</td><td>Add percentage (%) character to the output</td></tr></tbody></table>

<table><thead><tr><th>DATE_FORMAT string</th><th>Formatted date</th></tr></thead><tbody><tr><td>%Y-%m-%d</td><td>7/4/2013</td></tr><tr><td>%e/%c/%Y</td><td>4/7/2013</td></tr><tr><td>%c/%e/%Y</td><td>7/4/2013</td></tr><tr><td>%d/%m/%Y</td><td>4/7/2013</td></tr><tr><td>%m/%d/%Y</td><td>7/4/2013</td></tr><tr><td>%e/%c/%Y %H:%i</td><td>4/7/2013 11:20</td></tr><tr><td>%c/%e/%Y %H:%i</td><td>7/4/2013 11:20</td></tr><tr><td>%d/%m/%Y %H:%i</td><td>4/7/2013 11:20</td></tr><tr><td>%m/%d/%Y %H:%i</td><td>7/4/2013 11:20</td></tr><tr><td>%e/%c/%Y %T</td><td>4/7/2013 11:20</td></tr><tr><td>%c/%e/%Y %T</td><td>7/4/2013 11:20</td></tr><tr><td>%d/%m/%Y %T</td><td>4/7/2013 11:20</td></tr><tr><td>%m/%d/%Y %T</td><td>7/4/2013 11:20</td></tr><tr><td>%a %D %b %Y</td><td>Thu 4th Jul 2013</td></tr><tr><td>%a %D %b %Y %H:%i</td><td>Thu 4th Jul 2013 11:20</td></tr><tr><td>%a %D %b %Y %T</td><td>Thu 4th Jul 2013 11:20:05</td></tr><tr><td>%a %b %e %Y</td><td>Thu Jul 4 2013</td></tr><tr><td>%a %b %e %Y %H:%i</td><td>Thu Jul 4 2013 11:20</td></tr><tr><td>%a %b %e %Y %T</td><td>Thu Jul 4 2013 11:20:05</td></tr><tr><td>%W %D %M %Y</td><td>Thursday 4th July 2013</td></tr><tr><td>%W %D %M %Y %H:%i</td><td>Thursday 4th July 2013 11:20</td></tr><tr><td>%W %D %M %Y %T</td><td>Thursday 4th July 2013 11:20:05</td></tr><tr><td>%l:%i %p %b %e, %Y</td><td>7/4/2013 11:20</td></tr><tr><td>%M %e, %Y</td><td>4-Jul-13</td></tr><tr><td>%a, %d %b %Y %T</td><td>Thu, 04 Jul 2013 11:20:05</td></tr></tbody></table>

### DAYNAME

MySQL DAYNAME function returns the name of a weekday for a specified date. The following illustrates the syntax of the DAYNAME function:

```sql
mysql> SELECT DAYNAME('2000-01-01') dayname;
+----------+
| dayname  |
+----------+
| Saturday |
+----------+
1 row in set (0.00 sec)
```

```sql

mysql> SET @@lc_time_names = 'fr_FR';
Query OK, 0 rows affected (0.00 sec)

mysql> SELECT DAYNAME('2000-01-01') dayname;
+---------+
| dayname |
+---------+
| samedi  |
+---------+
1 row in set (0.00 sec)

```

### DAYOFWEEK

The DAYOFWEEK function returns the weekday index for a date i.e., 1 for Sunday, 2 for Monday, … 7 for Saturday. These index values correspond to the ODBC standard.

```sql
mysql> SELECT DAYNAME('2012-12-01'), DAYOFWEEK('2012-12-01');
+-----------------------+-------------------------+
| DAYNAME('2012-12-01') | DAYOFWEEK('2012-12-01') |
+-----------------------+-------------------------+
| Saturday              |                       7 |
+-----------------------+-------------------------+
1 row in set (0.00 sec)
```

### EXTRACT

The EXTRACT() function extracts part of a date. The following illustrates the syntax of the EXTRACT() function.

```sql
mysql> SELECT EXTRACT(DAY FROM '2017-07-14 09:04:44') DAY;
+------+
| DAY  |
+------+
|   14 |
+------+
1 row in set (0.00 sec)
```

The unit is the interval that you want to extract from the date. The following are the valid intervals for the unit argument.

> DAY, DAY_HOUR, DAY_MICROSECOND, DAY_MINUTE, DAY_SECOND, HOUR, HOUR_MICROSECOND, HOUR_MINUTE, HOUR_SECOND, MICROSECOND, MINUTE, MINUTE_MICROSECOND, MINUTE_SECOND, MONTH, QUARTER, SECOND, SECOND_MICROSECOND, WEEK, YEAR, YEAR_MONTH

### NOW

The MySQL NOW() function returns the current date and time in the configured time zone as a string or a number in the 'YYYY-MM-DD HH:MM:DD' or 'YYYYMMDDHHMMSS.uuuuuu' format.

```sql
SELECT NOW();
```

### MONTH

The MONTH function returns an integer that represents the month of a specified date value. The following illustrates the syntax of the MONTH function:

```sql
mysql> SELECT MONTH('2010-01-01');
+---------------------+
| MONTH('2010-01-01') |
+---------------------+
|                   1 |
+---------------------+
1 row in set (0.00 sec)
```

### STR_TO_DATE

The STR_TO_DATE() converts the str string into a date value based on the fmt format string. The STR_TO_DATE() function may return a DATE , TIME, or DATETIME value based on the input and format strings. If the input string is illegal, the STR_TO_DATE() function returns NULL.

```sql
SELECT STR_TO_DATE('21,5,2013','%d,%m,%Y');
> 2013-05-21
```

### SYSDATE

The SYSDATE() function returns the current date and time as a value in 'YYYY-MM-DD HH:MM:SS' format if the function is used in a string context or YYYYMMDDHHMMSS format in case the function is used in a numeric context.

```sql
mysql> SELECT SYSDATE();
+---------------------+
| SYSDATE()           |
+---------------------+
| 2017-07-13 17:42:37 |
+---------------------+
1 row in set (0.00 sec)
```

### TIMEDIFF

The TIMEDIFF returns the difference between two TIME or DATETIME values. See the following syntax of TIMEDIFF function.

```sql
mysql> SELECT TIMEDIFF('12:00:00','10:00:00') diff;
+----------+
| diff     |
+----------+
| 02:00:00 |
+----------+
1 row in set (0.00 sec)
```

### TIMESTAMPDIFF

The TIMESTAMPDIFF function returns the result of begin - end, where begin and end are DATE or DATETIME expressions.

The unit argument determines the unit of the result of (end - begin) represented as an integer. The following are valid units:

> MICROSECOND, SECOND, MINUTE, HOUR, DAY, WEEK, MONTH, QUARTER, YEAR

### WEEK

To check whether a particular date belongs to which week number, you use the WEEK function as follows:

```sql
SELECT WEEK(date, mode);
```

The WEEK function accepts two arguments:

- `date` is the date that you want to get a week number.
- `mode` is an optional argument that determines the logic of week number calculation. It allows you to specify whether the week should start on Monday or Sunday and the returned week number should be between 0 and 52 or 0 and 53.

If you ignore the mode argument, the WEEK function will use the value of the default_week_format system variable by default.

### WEEKDAY

The WEEKDAY function returns a weekday index for a date i.e., 0 for Monday, 1 for Tuesday, … 6 for Sunday.

```sql
mysql> SELECT DAYNAME('2010-01-01'), WEEKDAY('2010-01-01');
+-----------------------+-----------------------+
| DAYNAME('2010-01-01') | WEEKDAY('2010-01-01') |
+-----------------------+-----------------------+
| Friday                |                     4 |
+-----------------------+-----------------------+
1 row in set (0.00 sec)
```

### YEAR

The YEAR() function takes a date argument and returns the year of the date. See the syntax of the YEAR() function:

```sql
SELECT YEAR('2017-01-01');
 
+--------------------+
| YEAR('2017-01-01') |
+--------------------+
|               2017 |
+--------------------+
1 row in set (0.00 sec)
```

## Comparison functions

### COALESCE

The COALESCE function takes a number of arguments and returns the first non-NULL argument. In case all arguments are NULL, the COALESCE function returns NULL.

```sql
SELECT COALESCE(NULL, 0);  -- 0
SELECT COALESCE(NULL, NULL); -- NULL;
```

### GREATEST & LEAST

Both GREATEST and LEAST functions take N arguments and return the greatest and smallest values respectively. The following illustrates the syntax of the GREATEST and LEAST function:

```sql
SELECT GREATEST(10, 20, 30),  -- 30
       LEAST(10, 20, 30); -- 10
 
SELECT GREATEST(10, null, 30),  -- null
       LEAST(10, null , 30); -- null
```

### ISNULL

The ISNULL function takes one argument and tests whether that argument is NULL or not. The ISNULL function returns 1 if the argument is NULL, otherwise, it returns 0.

```sql
SELECT ISNULL(NULL); -- 1    
SELECT ISNULL(1);  -- 0
SELECT ISNULL(1 + NULL); -- 1;
SELECT ISNULL(1 / 0 ); -- 1;
```

## MATH functions

### ABS

The ABS() function is a mathematical function that returns the absolute (positive) value of a number.

```sql
SELECT 
    ABS(-10), 
    ABS(0), 
    ABS(10);  

> 10, 0, 10

```

### CEIL

The CEIL() function takes an input number and returns the smallest integer greater than or equal to that number.

```sql
SELECT CEIL(1.59);
--  2
SELECT CEIL(-1.59)
-- -1
```

### FLOOR

The FLOOR() function accepts one argument which can be number or numeric expression and returns the largest integer number less than or equal to the argument.

```sql
SELECT FLOOR(1.59);
--  1
SELECT FLOOR(-1.59)
-- -2
```

### MOD

The MOD() function returns the remainder of one number divided by another. The following shows the syntax of the MOD() function:

```sql
SELECT MOD(11, 3);
-- 2
```

### ROUND

The ROUND() is a mathematical function that allows you to round a number to a specified number of decimal places.

```sql
SELECT ROUND(20.5);
-- 21
SELECT ROUND(20.5, 0);
-- 21
SELECT ROUND(121.55,-2)
-- 100
```

### TRUNCATE

MySQL TRUNCATE() function truncates a number to a specified number of decimal places as shown below:

```sql
SELECT TRUNCATE(1.555,1);
--- 1.5
```

## Other functions

### LAST_INSERT_ID

In database design, you often use a surrogate key to generate unique integer values for the primary key column using the AUTO_INCREMENT attribute.

```sql
INSERT INTO tbl(description)
VALUES('MySQL last_insert_id');
```

```sql
SELECT LAST_INSERT_ID();
```

### CAST

The CAST() function converts a value of any type into a value that has a specified type. The target type can be any one of the following types: BINARY, CHAR, DATE, DATETIME, TIME,DECIMAL, SIGNED, UNSIGNED .

```sql
SELECT (1 + CAST('1' AS UNSIGNED))/2;
SELECT CONCAT('MySQL CAST example #',CAST(2 AS CHAR));
```