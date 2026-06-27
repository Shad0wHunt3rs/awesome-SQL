# Value window functions

Value window functions in SQL are a specific category of window functions that allow you to retrieve a value from a different row in the result set and display it alongside the current row. Unlike aggregate window functions (like SUM or AVG) which compute a statistical summary, value window functions look at specific positions in your data window to help you make direct row-to-row comparisons.


These are called **Value (Analytic) Window Functions** in SQL. They are used to **access values from other rows without collapsing the result set**.

## Types

1. `LEAD()`
2. `LAG()`
3. `FIRST_VALUE()`
4. `LAST_VALUE()`
5. `NTH_VALUE()`

---

## LEAD()

**Meaning**

`LEAD()` gives you the **next row’s value**.


**Syntax**

```sql
LEAD(column, offset, default) OVER (ORDER BY column)
```

* `offset` → how many rows ahead (default = 1)
* `default` → value if no next row exists

**Example**

| Name | Salary |
| ---- | ------ |
| A    | 100    |
| B    | 90     |
| C    | 80     |

```sql
SELECT
Name,
Salary,
LEAD(Salary) OVER (ORDER BY Salary DESC) AS next_salary
FROM Employee;
```

**Output**

| Name | Salary | Next Salary |
| ---- | ------ | ----------- |
| A    | 100    | 90          |
| B    | 90     | 80          |
| C    | 80     | NULL        |

---

### Use cases:

* Compare current vs next row
* Trend analysis
* Price drop detection

---

## LAG()

**Meaning**

`LAG()` gives you the **previous row’s value**.

**Syntax**:

```sql
LAG(column, offset, default) OVER (ORDER BY column)
```

**Example**

| Name | Salary |
| ---- | ------ |
| A    | 100    |
| B    | 90     |
| C    | 80     |

```sql
SELECT
Name,
Salary,
LAG(Salary) OVER (ORDER BY Salary DESC) AS prev_salary
FROM Employee;
```

**Output**

| Name | Salary | Prev Salary |
| ---- | ------ | ----------- |
| A    | 100    | NULL        |
| B    | 90     | 100         |
| C    | 80     | 90          |

---

### Use cases:

* Compare current vs previous value
* Growth analysis
* Difference calculation

Example:

```sql
Salary - LAG(Salary)
```

---

## FIRST_VALUE()

**Meaning**

Returns the **first value in the window (based on ORDER BY)**.

**Syntax**

```sql
FIRST_VALUE(column) OVER (ORDER BY column)
```

**Example**

| Name | Salary |
| ---- | ------ |
| A    | 100    |
| B    | 90     |
| C    | 80     |

```sql
SELECT
Name,
Salary,
FIRST_VALUE(Salary) OVER (ORDER BY Salary DESC) AS top_salary
FROM Employee;
```

**Output**

| Name | Salary | First Value |
| ---- | ------ | ----------- |
| A    | 100    | 100         |
| B    | 90     | 100         |
| C    | 80     | 100         |

### Use cases:

* Highest salary reference
* Baseline comparisons

---

## LAST_VALUE()

**Meaning**

Returns the **last value in the window**.


### ⚠️ Important Trick:

You MUST define window frame properly, otherwise it gives wrong results.

Correct version:

```sql
LAST_VALUE(column) OVER (
    ORDER BY column
    ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING
)
```

**Example**

| Name | Salary |
| ---- | ------ |
| A    | 100    |
| B    | 90     |
| C    | 80     |

```sql
SELECT
Name,
Salary,
LAST_VALUE(Salary) OVER (
    ORDER BY Salary DESC
    ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING
) AS last_salary
FROM Employee;
```

### Output:

| Name | Salary | Last Value |
| ---- | ------ | ---------- |
| A    | 100    | 80         |
| B    | 90     | 80         |
| C    | 80     | 80         |

### Use cases:

* Lowest value reference
* End-of-series comparison

---

## NTH_VALUE()

**Meaning**

`NTH_VALUE()` is a window function that returns the **Nth value from an ordered set of rows**.

**Syntax**

```sql
NTH_VALUE(column, N) OVER (
    ORDER BY column
)
```

* Returns the value at position **N** in the sorted window
* Value is repeated for all rows in the partition

**Employee**

| Name    | Salary |
| ------- | ------ |
| Alice   | 100000 |
| Bob     | 90000  |
| Charlie | 80000  |
| David   | 70000  |
| Eva     | 60000  |


```sql id="n1"
NTH_VALUE(Salary, 2) OVER (ORDER BY Salary DESC)
```

**Output**

| Name    | Salary | NTH_VALUE (2nd Highest) |
| ------- | ------ | ----------------------- |
| Alice   | 100000 | 90000                   |
| Bob     | 90000  | 90000                   |
| Charlie | 80000  | 90000                   |
| David   | 70000  | 90000                   |
| Eva     | 60000  | 90000                   |


### ⚠️ Important Trick:

* Requires proper `ORDER BY`
* Often needs full frame:

```sql
ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING
```

---

### Use cases

* 2nd/3rd highest salary
* Specific ranked value extraction
* Analytics reporting

---