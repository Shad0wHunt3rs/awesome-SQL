# Result Types


<img src="./1.png" width="500">

## Scalar Subquery

A **Scalar Subquery** returns **only one value** (one row and one column).

**Characteristics**

* Returns exactly **1 row × 1 column**.
* Used with operators like `=`, `>`, `<`, `>=`, `<=`, `<>`.
* Can be used in `SELECT`, `WHERE`, `HAVING`, and `SET` clauses.

**Example**

Find employees whose salary is greater than the average salary.

```sql
SELECT Name, Salary
FROM Employees
WHERE Salary >
(
    SELECT AVG(Salary)
    FROM Employees
);
```

**Inner Query Result**

| AVG(Salary) |
| ----------- |
| 60000       |

Since the subquery returns a **single value (60000)**, it is a **Scalar Subquery**.

---

## Row Subquery

A **Row Subquery** returns **one row with multiple columns**.

**Characteristics**

* Returns **1 row** but **more than one column**.
* Compared using row comparison operators.

**Example**

Suppose the Employees table is:

| EmployeeID | Name  | DepartmentID | Salary |
| ---------- | ----- | ------------ | ------ |
| 1          | Ali   | 1            | 50000  |
| 2          | Sara  | 2            | 70000  |
| 3          | Ahmed | 1            | 60000  |

Find the employee having the same DepartmentID and Salary as Ahmed.

```sql
SELECT Name
FROM Employees
WHERE (DepartmentID, Salary) =
(
    SELECT DepartmentID, Salary
    FROM Employees
    WHERE Name = 'Ahmed'
);
```

**Subquery Result**

| DepartmentID | Salary |
| ------------ | ------ |
| 1            | 60000  |

This returns **one row with two columns**, so it is a **Row Subquery**.

**Output**

| Name  |
| ----- |
| Ahmed |

---

## Table Subquery

A **Table Subquery** returns **multiple rows and/or multiple columns**.

**Characteristics**

* Returns a complete table (result set).
* Used with `IN`, `EXISTS`, `ANY`, `ALL`, or in the `FROM` clause.
* Can return:

  * Multiple rows
  * Multiple columns
  * Both

**Example 1: Multiple Rows**

Find employees working in departments 1 and 2.

```sql
SELECT Name
FROM Employees
WHERE DepartmentID IN
(
    SELECT DepartmentID
    FROM Departments
);
```

**Subquery Result**

| DepartmentID |
| ------------ |
| 1            |
| 2            |

This is a **Table Subquery** because it returns **multiple rows**.

**Example 2: Used in FROM Clause**

```sql
SELECT DepartmentID, AvgSalary
FROM
(
    SELECT DepartmentID,
           AVG(Salary) AS AvgSalary
    FROM Employees
    GROUP BY DepartmentID
) AS DeptAvg;
```

The inner query returns:

| DepartmentID | AvgSalary |
| ------------ | --------- |
| 1            | 55000     |
| 2            | 70000     |

Since it returns a **table**, it is a **Table Subquery**.

---
