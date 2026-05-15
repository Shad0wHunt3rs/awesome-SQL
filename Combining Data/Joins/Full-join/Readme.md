# FULL JOIN

`FULL JOIN` (also called `FULL OUTER JOIN`) returns:

* all rows from the left table
* all rows from the right table
* matched rows combined together
* unmatched rows filled with `NULL`

<img src="./1.png" width="600">

<br>

**Syntax**

```sql id="7f6d2a"
SELECT columns
FROM table1
FULL JOIN table2
ON table1.common_column = table2.common_column;
```

---

## How FULL JOIN Works

A `FULL JOIN`:

1. Keeps all rows from the left table
2. Keeps all rows from the right table
3. Matches rows where possible
4. Uses `NULL` where no match exists

---

# Important Note

Some databases like older versions of MySQL do **not** support `FULL JOIN` directly.

People often simulate it using:

```sql id="c8z3vf"
LEFT JOIN
UNION
RIGHT JOIN
```

---

## Example

<img src="./2.png" width="600">