# **GROUP BY**

The **`GROUP BY` clause** is used to **group rows that have the same values in one or more columns**.
It is mainly used with **aggregate functions** like `COUNT()`, `SUM()`, `AVG()`, `MAX()`, `MIN()` to perform calculations **on each group** instead of on the whole table.

```sql
SELECT column1, aggregate_function(column2)
FROM table_name
GROUP BY column1;
```

* `column1` → the column you want to group by
* `aggregate_function(column2)` → a calculation like `COUNT`, `SUM`, `AVG`, etc.

---

**Example**

Table: `students`

| name   | grade | marks |
| ------ | ----- | ----- |
| Ali    | A     | 90    |
| Sara   | A     | 85    |
| Hamza  | B     | 95    |
| Bilal  | B     | 80    |
| Ayesha | A     | 88    |

**Query: Count students in each grade**

```sql
SELECT grade, COUNT(*) AS total_students
FROM students
GROUP BY grade;
```

**Result:**

| grade | total_students |
| ----- | -------------- |
| A     | 3              |
| B     | 2              |

* Rows are **grouped by `grade`**
* `COUNT(*)` counts the number of students in each group

---

## **Using GROUP BY with SUM or AVG**

**Query: Average marks per grade**

```sql
SELECT grade, AVG(marks) AS avg_marks
FROM students
GROUP BY grade;
```

**Result:**

| grade | avg_marks |
| ----- | --------- |
| A     | 87.67     |
| B     | 87.50     |

* Groups rows by `grade`
* Calculates **average marks** for each group

---

## **Notes About GROUP BY**

* `GROUP BY` **must include all columns** in `SELECT` that are **not inside aggregate functions**
* Often used with **HAVING** to filter groups
* The order of rows can also be controlled with `ORDER BY`

---
