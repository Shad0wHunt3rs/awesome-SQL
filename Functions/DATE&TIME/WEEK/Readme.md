# `WEEK()`

Returns the week number of the year from a date

**Syntax**

```sql id="w1"
SELECT WEEK(date);
```

---

**Example**

```sql id="w2"
SELECT WEEK('2026-05-21');
```

Result:

```text id="w3"
20
```

---


## Important points

* Returns week number (`0–53`)
* Works with `DATE`, `DATETIME`, `TIMESTAMP`
* Different SQL modes may calculate weeks differently
* If value is `NULL`, result is `NULL`

---
