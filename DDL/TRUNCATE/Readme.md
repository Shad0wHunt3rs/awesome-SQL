# **TRUNCATE in SQL**

**TRUNCATE** is a DDL command used to **delete all rows from a table instantly**, while **keeping the table structure**.

* Removes **all data** from the table
* Keeps columns, constraints, and table structure
* Resets AUTO_INCREMENT values
* Works very fast (faster than DELETE)


```sql
TRUNCATE TABLE table_name;
```

**Example:**

```sql
TRUNCATE TABLE person;
```

>[!NOTE]
> You **cannot undo** TRUNCATE (auto-commit)
> You **cannot use WHERE** (no filtering)
> You **cannot truncate** a table if another table references it with a foreign key



**Why TRUNCATE is DDL**

TRUNCATE resets the table by deallocating all data pages, which changes the **structure/storage**, not just rows.
Because it affects the table at the schema/storage level, it is classified as a **DDL command**.

**Why DELETE is NOT DDL**

DELETE removes rows **one by one**, only affecting the **data**, not the structure.
Since it works at the **DML (data manipulation)** level, it is classified as a **DML command**, not DDL.



---

