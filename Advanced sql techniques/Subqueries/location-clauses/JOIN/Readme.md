# Subquery in the `JOIN` Clause

A **subquery in the `JOIN` clause** is a subquery that is used as a **derived table (temporary table)** and is joined with another table using SQL `JOIN` operations. It is useful when you need to join a table with calculated or aggregated data instead of the original table.

The subquery executes first, produces a temporary result set, and then the outer query joins it with another table.

> [!Note] 
> A subquery used in a `JOIN` must have an **alias**, as it is treated like a temporary table.

---

**Syntax**

```sql
SELECT column_list
FROM table1 t1
JOIN
(
    SELECT column_list
    FROM table2
    WHERE condition
) AS alias_name
ON t1.column_name = alias_name.column_name;
```

---

# Example 1: Join Employees with Average Department Salary

**Employees**

| EmployeeID | Name  | DepartmentID | Salary |
| ---------- | ----- | ------------ | ------ |
| 1          | Ali   | 1            | 50000  |
| 2          | Sara  | 2            | 70000  |
| 3          | Ahmed | 1            | 60000  |
| 4          | John  | 2            | 80000  |

### Query

```sql
SELECT e.Name,
       e.Salary,
       d.AvgSalary
FROM Employees e
JOIN
(
    SELECT DepartmentID,
           AVG(Salary) AS AvgSalary
    FROM Employees
    GROUP BY DepartmentID
) AS d
ON e.DepartmentID = d.DepartmentID;
```

### How it Works

**Step 1:** The subquery executes first.

```sql
SELECT DepartmentID,
       AVG(Salary) AS AvgSalary
FROM Employees
GROUP BY DepartmentID;
```

**Subquery Result**

| DepartmentID | AvgSalary |
| ------------ | --------- |
| 1            | 55000     |
| 2            | 75000     |

**Step 2:** The outer query joins this temporary table with the `Employees` table using `DepartmentID`.

### Output

| Name  | Salary | AvgSalary |
| ----- | ------ | --------- |
| Ali   | 50000  | 55000     |
| Ahmed | 60000  | 55000     |
| Sara  | 70000  | 75000     |
| John  | 80000  | 75000     |

---

# Example 2: Compare Employee Salary with Department Average

```sql
SELECT e.Name,
       e.Salary,
       d.AvgSalary
FROM Employees e
JOIN
(
    SELECT DepartmentID,
           AVG(Salary) AS AvgSalary
    FROM Employees
    GROUP BY DepartmentID
) AS d
ON e.DepartmentID = d.DepartmentID
WHERE e.Salary > d.AvgSalary;
```

### Output

| Name  | Salary | AvgSalary |
| ----- | ------ | --------- |
| Ahmed | 60000  | 55000     |
| John  | 80000  | 75000     |

Only employees whose salary is greater than the average salary of their department are displayed.

---

# Example 3: Join Employees with Department Details

**Departments**

| DepartmentID | DepartmentName |
| ------------ | -------------- |
| 1            | HR             |
| 2            | IT             |

```sql
SELECT e.Name,
       d.DepartmentName
FROM Employees e
JOIN
(
    SELECT DepartmentID,
           DepartmentName
    FROM Departments
) AS d
ON e.DepartmentID = d.DepartmentID;
```

### Output

| Name  | DepartmentName |
| ----- | -------------- |
| Ali   | HR             |
| Ahmed | HR             |
| Sara  | IT             |
| John  | IT             |

Although this example could be written without a subquery, it demonstrates that a subquery can also be used in a `JOIN` clause.

---

# Why Use a Subquery in the `JOIN` Clause?

A subquery in a `JOIN` is useful when:

* You need to join with **aggregated data** (such as averages or totals).
* You want to **filter or transform data** before joining it.
* You want to simplify complex queries by separating calculations from the main query.

---

# Key Points

* A subquery in the **`JOIN` clause** acts as a **temporary table (derived table)**.
* It is joined with another table using `JOIN` conditions.
* The subquery executes **before** the outer query.
* **An alias is mandatory** for the subquery.
* It commonly returns **multiple rows and multiple columns**.

---

# Advantages

* Makes complex joins easier to understand.
* Allows joining with aggregated or filtered data.
* Improves readability by separating calculations from the main query.
* Helps reuse intermediate results without creating a permanent table.

---

# Limitation

A subquery used in a `JOIN` **must have an alias**.

**Incorrect Query**

```sql
SELECT e.Name,
       d.AvgSalary
FROM Employees e
JOIN
(
    SELECT DepartmentID,
           AVG(Salary) AS AvgSalary
    FROM Employees
    GROUP BY DepartmentID
)
ON e.DepartmentID = DepartmentID;
```

**Error**

```text
Every derived table must have its own alias.
```

**Correct Query**

```sql
SELECT e.Name,
       d.AvgSalary
FROM Employees e
JOIN
(
    SELECT DepartmentID,
           AVG(Salary) AS AvgSalary
    FROM Employees
    GROUP BY DepartmentID
) AS d
ON e.DepartmentID = d.DepartmentID;
```

Here, `d` is the alias for the derived table, allowing the outer query to reference its columns correctly.
