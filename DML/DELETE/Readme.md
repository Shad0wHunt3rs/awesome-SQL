# **DELETE**

`DELETE` is a **DML (Data Manipulation Language)** command used to **remove existing rows** from a table.

> **Important:** `DELETE` removes **rows**, not the table structure. The table itself and its columns remain intact.

```sql
DELETE FROM table_name
WHERE condition;
```

* `table_name` → the table from which you want to delete rows
* `condition` → specifies which rows to delete


### **Deleting Specific Rows**

```sql
DELETE FROM customers
WHERE score = 0;
```

* Deletes only rows where `score = 0`
* Other rows remain untouched


### **Deleting All Rows**

```sql
DELETE FROM customers;
```

* Deletes **all rows** in the table
* Table structure (columns, constraints, indexes) stays the same
* Works, but in **safe update mode**, MySQL may block it if no `WHERE` clause uses a key

> **Tip:** To delete all rows faster and reset auto-increment in MySQL, use `TRUNCATE` instead.


### **DELETE with Conditions**

You can use operators:

```sql
DELETE FROM customers
WHERE country = 'Palestine' AND score < 1000;
```

* Deletes only rows that match **both conditions**


### **DELETE with LIMIT (MySQL specific)**

```sql
DELETE FROM customers
WHERE country = 'Palestine'
LIMIT 10;
```

* Deletes only **10 rows at a time**
* Useful to avoid locking the entire table


### **DELETE and Transactions**

Since `DELETE` is **DML**, you can **rollback** changes if inside a transaction:

```sql
START TRANSACTION;

DELETE FROM customers
WHERE score = 0;

ROLLBACK;   -- undoes the deletion
```

* If you run `COMMIT`, deletion becomes permanent

---

## **DELETE vs TRUNCATE**

| Feature                 | DELETE               | TRUNCATE                 |
| ----------------------- | -------------------- | ------------------------ |
| Removes rows            | Yes                  | Yes                      |
| Removes table structure | No                   | No                       |
| Can rollback            | Yes (in transaction) | Usually No               |
| Can use WHERE           | Yes                  | No                       |
| Slower / faster         | Slower (row by row)  | Fast (deallocates pages) |

---

## **Common Errors**

* **No WHERE clause in safe mode** (MySQL 1175)
* Trying to delete from a **table with foreign key restrictions** → may fail

Example:

```sql
DELETE FROM orders
WHERE customer_id = 1;
```

* Will fail if `orders` has a foreign key reference that prevents deletion

