# GROUP_CONCAT separator

When using `GROUP_CONCAT`, you can specify a custom separator

```sql
SELECT 
	GROUP_CONCAT(
		a.`field`
		SEPARATOR '␟'
	) AS `fields`;
```
