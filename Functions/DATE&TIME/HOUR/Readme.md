# `HOUR()`

Extracts the hour part from a time or datetime

**Syntax**

```sql id="h1"
SELECT HOUR(time);
```

---

**Example**

```sql id="h2"
SELECT HOUR('15:45:30');
```

Result:

```text id="h3"
15
```

---


## Important points

* Returns hour value (`0–23`)
* Works with `TIME`, `DATETIME`, `TIMESTAMP`
* If value is `NULL`, result is `NULL`

---
