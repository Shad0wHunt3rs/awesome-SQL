# `MINUTE()`

Extracts the minute part from a time or datetime

**Syntax**

```sql id="m1"
SELECT MINUTE(time);
```

---

## Example

```sql id="m2"
SELECT MINUTE('15:45:30');
```

Result:

```text id="m3"
45
```

---

## Important points

* Returns minute value (`0–59`)
* Works with `TIME`, `DATETIME`, `TIMESTAMP`
* If value is `NULL`, result is `NULL`

---
