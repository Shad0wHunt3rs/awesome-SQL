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

<br>
<br>


<img src="./GROUP BY.png" width="600">


here we have grouped the orignal data by using the country 


<br>
<br>


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


>[!NOTE]
> if you donot use the `AS(ALIAS)` here the column as COUNT(*) but if you use ALIAS it will be `total_students`

<img src="./GROUP BY1.png" width="400">

---


## **Notes About GROUP BY**

* `GROUP BY` **must include all columns** in `SELECT` that are **not inside aggregate functions**
* Often used with **HAVING** to filter groups
* The order of rows can also be controlled with `ORDER BY`

---
