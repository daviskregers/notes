# JSONOBJECTAGG() alternative in MariaDB

While the function is supported in MySQL, it is not in MariaDB. The workaround is to use something like this:

NOTE: this will not work with strings that have quotes in them, it will render a broken JSON.

```sql
SELECT
 CONCAT("{", GROUP_CONCAT(DISTINCT CONCAT('"', 'key', '": "',
                      'value', '"') SEPARATOR ', '), "}") json
```

![mariadb_jsonobjagg_example.png](../../images/mariadb_jsonobjagg_example.png)
