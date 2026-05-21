# `DAY()`

Extracts the day of the month from a date or datetime

**Syntax**

```sql id="d1"
SELECT DAY(date);
```

---

**Example**

```sql id="d2"
SELECT DAY('2026-05-21');
```

Result:

```text id="d3"
21
```

---

## Important points

* Returns day number from `1` to `31`
* Works with `DATE`, `DATETIME`, and `TIMESTAMP`
* If value is `NULL`, result is `NULL`

---