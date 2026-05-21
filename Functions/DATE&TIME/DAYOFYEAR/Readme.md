# `DAYOFYEAR()`

Returns the day number of the year from a date

**Syntax**

```sql id="dy1"
SELECT DAYOFYEAR(date);
```

---

**Example**

```sql id="dy2"
SELECT DAYOFYEAR('2026-05-21');
```

Result:

```text id="dy3"
141
```

---

## Important points

* Returns values from `1` to `365` (or `366` in leap year)
* Works with `DATE`, `DATETIME`, `TIMESTAMP`
* If value is `NULL`, result is `NULL`

---
