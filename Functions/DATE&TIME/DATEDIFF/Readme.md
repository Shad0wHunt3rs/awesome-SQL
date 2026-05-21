# `DATEDIFF()`

Returns the difference between two dates (in days)

**Syntax**

```sql id="d1"
SELECT DATEDIFF(date1, date2);
```

---

**Example**

```sql id="d2"
SELECT DATEDIFF('2026-05-30', '2026-05-21');
```

Result:

```text id="d3"
9
```

---

## Important points

* Returns result in **days only**
* Time part is ignored (only date matters)
* Works with `DATE`, `DATETIME`, `TIMESTAMP`
* If any value is `NULL`, result is `NULL`

---

**order matters**

```sql id="d4"
SELECT DATEDIFF('2026-05-21', '2026-05-30');
```

Result:

```text id="d5"
-9
```

---
