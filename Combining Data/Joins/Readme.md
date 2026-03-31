<!-- # **Joins in SQL**

A **join** in SQL is used to combine rows from **two or more tables** based on a related column between them. Joins are primarily used to **fetch data across multiple tables** without duplicating data.

---

## **1. INNER JOIN**

**Definition:**
Returns only the rows where there is a **match in both tables**.

**Syntax:**

```sql
SELECT table1.column1, table1.column2, table2.column1, table2.column2
FROM table1
INNER JOIN table2
ON table1.common_column = table2.common_column;
```

**Example:**
We have two tables:

**Customers**

| id  | name    |
| --- | ------- |
| 1   | Alice   |
| 2   | Bob     |
| 3   | Charlie |

**Orders**

| id  | customer_id | product  |
| --- | ----------- | -------- |
| 1   | 1           | Laptop   |
| 2   | 2           | Mouse    |
| 3   | 4           | Keyboard |

**Query:**

```sql
SELECT Customers.name, Orders.product
FROM Customers
INNER JOIN Orders
ON Customers.id = Orders.customer_id;
```

**Result:**

| name  | product |
| ----- | ------- |
| Alice | Laptop  |
| Bob   | Mouse   |

✅ Only customers with orders appear. Charlie is excluded because there’s no matching order.

---

## **2. LEFT JOIN (or LEFT OUTER JOIN)**

**Definition:**
Returns **all rows from the left table**, and the matching rows from the right table. If no match exists, the right table columns return `NULL`.

**Syntax:**

```sql
SELECT table1.column1, table2.column2
FROM table1
LEFT JOIN table2
ON table1.common_column = table2.common_column;
```

**Example:**

```sql
SELECT Customers.name, Orders.product
FROM Customers
LEFT JOIN Orders
ON Customers.id = Orders.customer_id;
```

**Result:**

| name    | product |
| ------- | ------- |
| Alice   | Laptop  |
| Bob     | Mouse   |
| Charlie | NULL    |

✅ Charlie is included even though there’s no order.

---

## **3. RIGHT JOIN (or RIGHT OUTER JOIN)**

**Definition:**
Returns **all rows from the right table**, and the matching rows from the left table. If no match exists, left table columns return `NULL`.

**Syntax:**

```sql
SELECT table1.column1, table2.column2
FROM table1
RIGHT JOIN table2
ON table1.common_column = table2.common_column;
```

**Example:**

```sql
SELECT Customers.name, Orders.product
FROM Customers
RIGHT JOIN Orders
ON Customers.id = Orders.customer_id;
```

**Result:**

| name  | product  |
| ----- | -------- |
| Alice | Laptop   |
| Bob   | Mouse    |
| NULL  | Keyboard |

✅ The order with customer_id 4 appears even though there’s no matching customer.

---

## **4. FULL OUTER JOIN**

**Definition:**
Returns **all rows from both tables**. Where there’s no match, columns return `NULL`.

**Syntax (supported in PostgreSQL, SQL Server):**

```sql
SELECT table1.column1, table2.column2
FROM table1
FULL OUTER JOIN table2
ON table1.common_column = table2.common_column;
```

**Example:**

```sql
SELECT Customers.name, Orders.product
FROM Customers
FULL OUTER JOIN Orders
ON Customers.id = Orders.customer_id;
```

**Result:**

| name    | product  |
| ------- | -------- |
| Alice   | Laptop   |
| Bob     | Mouse    |
| Charlie | NULL     |
| NULL    | Keyboard |

✅ Combines **LEFT JOIN + RIGHT JOIN** behavior.

---

## **5. CROSS JOIN**

**Definition:**
Returns the **Cartesian product** of both tables. Every row from the first table is combined with every row from the second table.

**Syntax:**

```sql
SELECT table1.column1, table2.column2
FROM table1
CROSS JOIN table2;
```

**Example:**

```sql
SELECT Customers.name, Orders.product
FROM Customers
CROSS JOIN Orders;
```

**Result (all combinations):**

| name    | product  |
| ------- | -------- |
| Alice   | Laptop   |
| Alice   | Mouse    |
| Alice   | Keyboard |
| Bob     | Laptop   |
| Bob     | Mouse    |
| Bob     | Keyboard |
| Charlie | Laptop   |
| Charlie | Mouse    |
| Charlie | Keyboard |

⚠️ Use carefully with large tables because the result grows **multiplicatively**.

---

## **6. SELF JOIN**

**Definition:**
A **self join** joins a table to itself. Useful for hierarchical data or comparing rows in the same table.

**Syntax:**

```sql
SELECT a.column1, b.column2
FROM table_name a
JOIN table_name b
ON a.common_column = b.common_column;
```

**Example:**
Suppose we have **Employees** table:

| emp_id | name  | manager_id |
| ------ | ----- | ---------- |
| 1      | John  | NULL       |
| 2      | Alice | 1          |
| 3      | Bob   | 1          |

Query to find employees with their manager:

```sql
SELECT e1.name AS Employee, e2.name AS Manager
FROM Employees e1
LEFT JOIN Employees e2
ON e1.manager_id = e2.emp_id;
```

**Result:**

| Employee | Manager |
| -------- | ------- |
| John     | NULL    |
| Alice    | John    |
| Bob      | John    |

✅ Self join allows referencing the same table with aliases.

---

## **7. NATURAL JOIN**

**Definition:**
Automatically joins tables based on **columns with the same name** in both tables. Avoids specifying `ON`.

**Syntax:**

```sql
SELECT *
FROM table1
NATURAL JOIN table2;
```

**⚠️ Warning:**

* Can be dangerous if table schemas change.
* Explicit `JOIN ... ON` is usually safer.

---

## **Quick Comparison Table**

| Join Type       | Includes rows with match | Includes unmatched left | Includes unmatched right | Both unmatched |
| --------------- | ------------------------ | ----------------------- | ------------------------ | -------------- |
| INNER JOIN      | ✅ Yes                    | ❌ No                    | ❌ No                     | ❌ No           |
| LEFT JOIN       | ✅ Yes                    | ✅ Yes                   | ❌ No                     | ❌ No           |
| RIGHT JOIN      | ✅ Yes                    | ❌ No                    | ✅ Yes                    | ❌ No           |
| FULL OUTER JOIN | ✅ Yes                    | ✅ Yes                   | ✅ Yes                    | ✅ Yes          |
| CROSS JOIN      | All combinations         | —                       | —                        | —              |
| SELF JOIN       | Depends on join          | —                       | —                        | —              |

---

## **Tips for Using Joins**

1. Always use **ON** to specify join conditions (except NATURAL JOIN).
2. Use **table aliases** (`t1`, `t2`) to make queries readable.
3. LEFT/RIGHT joins are useful when you **don’t want to lose unmatched data**.
4. INNER JOIN is the most common for **filtering only matching data**.
5. CROSS JOIN is rarely used but useful for **all combinations**, e.g., generating test data.
6. Self joins are great for **hierarchies, parent-child relations, or comparing rows** in the same table.

---

If you want, I can make a **single markdown file** with **all joins and examples**, ready to save for SQL reference.

Do you want me to do that? -->
