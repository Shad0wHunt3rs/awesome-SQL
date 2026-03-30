#**RENAME in SQL?**

RENAME is a **DDL operation** used to change the **name of a database object** (mainly a table).

To give a table a new name without changing its data, columns, or structure.

It updates the **metadata** so the database now knows the table by a new name.


```sql
RENAME TABLE old_name TO new_name;
```

OR using ALTER:

```sql
ALTER TABLE old_name RENAME TO new_name;
```
