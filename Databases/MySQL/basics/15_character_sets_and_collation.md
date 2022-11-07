# Character set and collation

## Character set

```sql
SHOW CHARACTER SET
```

```sql
SET @str = CONVERT('MySQL Character Set' USING ucs2);
SELECT LENGTH(@str), CHAR_LENGTH(@str);
```

```sql
CONVERT(expression USING character_set_name)
CAST(string AS character_type CHARACTER SET character_set_name)
SELECT CAST(_latin1'MySQL character set' AS CHAR CHARACTER SET utf8);
```

```sql
SET NAMES 'utf8';
```

## Collation

```sql
SHOW COLLATION LIKE 'character_set_name%';
```
```sql
SHOW COLLATION LIKE 'latin1%';
```

```sql
ALTER TABLE t1
CHARACTER SET latin1
COLLATE latin1_german1_ci;
```

```sql
ALTER TABLE t2
MODIFY c1 VARCHAR(25)
CHARACTER SET latin1;
```