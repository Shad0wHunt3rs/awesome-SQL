# Ranking Window Functions

Ranking Window Functions are SQL window functions that assign a rank or sequence number to rows based on a specified ordering. Unlike aggregate functions, they do not collapse rows—they calculate a value for each row while preserving the original result set.

## TYPES

1. **ROW_NUMBER()**
2. **RANK()**
3. **DENSE_RANK()**
4. **CUME_DIST()**
5. **PERCENT_RANK()**
6. **NTILE(n)**


---


## ROW_NUMBER()

**Definition**

`ROW_NUMBER()` assigns a **unique sequential number** to each row.

Even if two rows have the same value, each gets a different number.

**Syntax**

```sql
SELECT
Name,
Salary,
ROW_NUMBER() OVER(ORDER BY Salary DESC) AS RowNo
FROM Employee;
```

**Output**

| Name    | Salary | Row Number |
| ------- | ------ | ---------- |
| Alice   | 90000  | 1          |
| Bob     | 85000  | 2          |
| Charlie | 85000  | 3          |
| David   | 70000  | 4          |
| Eva     | 65000  | 5          |
| Frank   | 65000  | 6          |

Notice:

Bob and Charlie have the same salary.

Still,

```
Bob      2
Charlie  3
```

because every row gets a unique number.

**Characteristics**

* No duplicate numbers
* No skipped numbers
* Always unique

---

#### Uses

**Pagination**

Pagination is the process of dividing a large result set into smaller pages instead of displaying all rows at once.

```sql
SELECT *,
ROW_NUMBER() OVER(ORDER BY Salary DESC) AS rn
FROM Employee;
```

Suppose:

Page Size = 3
Page Number = 2

We want rows 4–6.

```sql
WITH EmployeeData AS
(
    SELECT
        EmpID,
        Name,
        Salary,
        ROW_NUMBER() OVER(ORDER BY Salary DESC) AS RowNum
    FROM Employee
)
SELECT *
FROM EmployeeData
WHERE RowNum BETWEEN 4 AND 6;
```


**Remove Duplicate Records**

```sql
WITH CTE AS
(
SELECT *,
ROW_NUMBER() OVER(
PARTITION BY Email
ORDER BY ID
) rn
FROM Customer
)

DELETE
FROM CTE
WHERE rn>1;
```

---

## RANK()

**Definition**

`RANK()` assigns the same rank to rows having equal values.

After a tie, rank numbers are skipped.

**Syntax**

```sql
SELECT
Name,
Salary,
RANK() OVER(ORDER BY Salary DESC) RankNo
FROM Employee;
```

**Output**

| Name    | Salary | Rank |
| ------- | ------ | ---- |
| Alice   | 90000  | 1    |
| Bob     | 85000  | 2    |
| Charlie | 85000  | 2    |
| David   | 70000  | 4    |
| Eva     | 65000  | 5    |
| Frank   | 65000  | 5    |

Notice

```
1
2
2
4
5
5
```

Rank **3** is skipped because two employees share Rank 2.


---

#### Uses

* Sports rankings
* Examination rankings
* Competitions

Example

```
Gold
Silver
Silver
Bronze
```

Ranks become

```
1
2
2
4
```

---

## DENSE_RANK()

**Definition**

Like `RANK()`, but **does not skip numbers** after ties.

**Syntax**

```sql
SELECT
Name,
Salary,
DENSE_RANK() OVER(
ORDER BY Salary DESC
) DenseRank
FROM Employee;
```

**Output**

| Name    | Salary | Dense Rank |
| ------- | ------ | ---------- |
| Alice   | 90000  | 1          |
| Bob     | 85000  | 2          |
| Charlie | 85000  | 2          |
| David   | 70000  | 3          |
| Eva     | 65000  | 4          |
| Frank   | 65000  | 4          |

Notice

```
1
2
2
3
4
4
```

No skipped ranks.

### Uses

* Top N employees
* Product ranking
* Customer ranking

---

## CUME_DIST()

**Definition**

`CUME_DIST()` stands for **Cumulative Distribution**.

It tells you the proportion (fraction) of rows whose value is **less than or equal to** the current row.


**Formula:**


```bash
CUME_DIST = (Number of rows with value ≤ Current Value) ÷ (Total Rows)
```

The result is between **0 and 1**.

**Example**

Marks

| Student | Marks |
| ------- | ----- |
| A       | 95    |
| B       | 90    |
| C       | 90    |
| D       | 80    |
| E       | 70    |

Query

```sql
SELECT
Marks,
CUME_DIST() OVER(
ORDER BY Marks DESC
) AS CD
FROM Student;
```

**Output**

| Marks | Rows ≤ Current (in DESC order) | CUME_DIST  |
| ----- | ------------------------------ | ---------- |
| 95    | 1                              | 1/5 = 0.20 |
| 90    | 3                              | 3/5 = 0.60 |
| 90    | 3                              | 3/5 = 0.60 |
| 80    | 4                              | 4/5 = 0.80 |
| 70    | 5                              | 5/5 = 1.00 |

---

Meaning

For marks 90,

```
60% of students
have marks greater than or equal to 90
```

(depending on the ordering direction).


#### Uses

* Percentile calculations
* Student performance
* Salary distribution

---

## PERCENT_RANK()

**Definition**

Shows the relative rank of a row as a percentage between 0 and 1.

**Formula**

```text
PERCENT_RANK = (Rank - 1) / (Total Rows - 1)
```

The first row always has a value of **0**.

The last row always has a value of **1** (if there is more than one row).

**Example**

Scores

```
100
90
90
80
70
```

Ranks

```
1
2
2
4
5
```

Total rows = 5

Calculations

For 100

```
(1-1)/(5-1)=0
```

For 90

```
(2-1)/4

0.25
```

For 80

```
(4-1)/4

0.75
```

For 70

```
(5-1)/4

1.00
```


Output

| Marks | Rank | Percent Rank |
| ----- | ---- | ------------ |
| 100   | 1    | 0.00         |
| 90    | 2    | 0.25         |
| 90    | 2    | 0.25         |
| 80    | 4    | 0.75         |
| 70    | 5    | 1.00         |


#### Uses

* Relative ranking
* Percentile reports
* Data analytics

---

## NTILE(n)

**Definition**

Divides rows into **n approximately equal groups (tiles or buckets)**.

**Syntax**

```sql
NTILE(4)
```

Creates four groups.


Example

Six employees

```sql
SELECT
Name,
Salary,
NTILE(3) OVER(
ORDER BY Salary DESC
) Bucket
FROM Employee;
```

Output

| Name    | Salary | Bucket |
| ------- | ------ | ------ |
| Alice   | 90000  | 1      |
| Bob     | 85000  | 1      |
| Charlie | 85000  | 2      |
| David   | 70000  | 2      |
| Eva     | 65000  | 3      |
| Frank   | 65000  | 3      |

Each bucket has two rows.

---

Suppose there are ten rows.

```sql
NTILE(4)
```

Output

```
Bucket 1 → 3 rows

Bucket 2 → 3 rows

Bucket 3 → 2 rows

Bucket 4 → 2 rows
```

The earlier buckets receive one extra row when the rows cannot be divided evenly.


## Uses

* Divide customers into quartiles
* Top 25%
* Bottom 10%
* Salary bands
* Market segmentation

---


## Complete Comparison

| Function         | Duplicate Values                      | Gaps in Rank      | First Value | Last Value                | Main Purpose                                                              |
| ---------------- | ------------------------------------- | ----------------- | ----------- | ------------------------- | ------------------------------------------------------------------------- |
| `ROW_NUMBER()`   | No                                    | No                | 1           | N                         | Unique sequence for every row                                             |
| `RANK()`         | Yes                                   | Yes               | 1           | Depends on ties           | Competition-style ranking                                                 |
| `DENSE_RANK()`   | Yes                                   | No                | 1           | Number of distinct values | Ranking without gaps                                                      |
| `CUME_DIST()`    | Same values get the same distribution | N/A               | 1/N         | 1                         | Cumulative distribution (fraction of rows at or before the current value) |
| `PERCENT_RANK()` | Same values get the same percentage   | Based on `RANK()` | 0           | 1                         | Relative rank between 0 and 1                                             |
| `NTILE(n)`       | N/A                                   | N/A               | 1           | n                         | Divide rows into approximately equal-sized buckets                        |

