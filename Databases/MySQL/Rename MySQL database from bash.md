---
Created: 2022-11-11 06:39:04
Modified: Wednesday 9th November 2022 10:49:06
Type: article
Source: https://phoenixnap.com/kb/how-to-rename-a-mysql-database
Tags: [conspect, review]
Review: Hard
---

You can use a following command to rename databases in bash.

```console
mysql -u USER -pPASSWORD OLDDB -sNe 'show tables' | while read table; do mysql -u USER -pPASSWORD NEWDB -sNe "RENAME TABLE \`OLDDB\`.$table TO \`NEWDB\`.$table"; done
```