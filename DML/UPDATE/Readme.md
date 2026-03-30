# **UPDATE**

`UPDATE` is a **DML (Data Manipulation Language)** command used to **modify existing rows** in a table.

It does *not* change the structure of the table — only the **data**.

```sql
UPDATE table_name
SET column1 = value1, column2 = value2
WHERE condition;
```

---

### **Updating a Single Column**

```sql
UPDATE students
SET class = '10th'
WHERE id = 1;
```

This changes only the `class` of the row where `id = 1`.

---

### **Updating Multiple Columns**

```sql
UPDATE students
SET name = 'Ali', class = '9th'
WHERE id = 2;
```

Both columns are updated at the same time.

---

### **Updating ALL Rows (Without WHERE)**

```sql
UPDATE students
SET class = 'Unknown';
```

>[!WARNING]
> Without a `WHERE` clause, *every row* in the table will be updated.

---

### **UPDATE With a Condition**

You can update rows that match specific criteria:

```sql
UPDATE students
SET class = '10th'
WHERE name = 'Ali';
```

---

### **UPDATE Using Expressions**

You can use math and functions:

```sql
UPDATE employees
SET salary = salary + 5000;
```

Increases every employee’s salary by 5000.

---


### **UPDATE + DEFAULT**

The `DEFAULT` keyword can be used:

```sql
UPDATE students
SET class = DEFAULT
WHERE id = 5;
```

If the column has a default defined, it will be applied.

---

### **UPDATE and Transactions**

Because `UPDATE` is DML, you can **rollback** changes if they are inside a transaction.

```sql
START TRANSACTION;

UPDATE students
SET class = '9th'
WHERE id = 1;

ROLLBACK;   -- undo the update
```

If you run `COMMIT`, the update becomes permanent.

---

## **Common Errors in UPDATE**

- **Updating a NOT NULL column with NULL**

```sql
UPDATE students SET class = NULL;   -- error if NOT NULL
```

- **Missing WHERE causing full table update**

This is the most common mistake:

```sql
UPDATE students SET class = 'Fail';
```

All rows will change.

---
