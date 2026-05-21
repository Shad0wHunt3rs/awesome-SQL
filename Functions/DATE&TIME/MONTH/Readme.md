# `MONTH()`

Extracts the month from a date or datetime

**Syntax**

```sql id="m1"
SELECT MONTH(date);
```

---

**Example**

```sql id="m2"
SELECT MONTH('2026-05-21');
```

Result:

```id="xk3n91"
5
```

---

## Using table data

```sql id="m3"
SELECT order_date, MONTH(order_date)
FROM orders;
```

---

## Important points

* Returns month as a number (1–12)
* Works on `DATE`, `DATETIME`, `TIMESTAMP`
* If value is `NULL`, result is `NULL`

---