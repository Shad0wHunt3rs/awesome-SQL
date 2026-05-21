# `YEAR()`

Extracts the year part from a date or datetime

**Syntax**

```sql id="y1"
SELECT YEAR(date);
```

---

**Example**

```sql id="y2"
SELECT YEAR('2026-05-21');
```

Result:

```
2026
```

---

## Using table data

```sql id="y3"
SELECT order_date, YEAR(order_date)
FROM orders;
```

---

## Important points

* Works on `DATE`, `DATETIME`, `TIMESTAMP`
* Returns only the **year (YYYY)**
* If value is `NULL`, result is `NULL`

---
