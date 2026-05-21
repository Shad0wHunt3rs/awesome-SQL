# `QUARTER()`

Returns the quarter of the year from a date

**Syntax**

```sql id="q1"
SELECT QUARTER(date);
```

---

**Example**

```sql id="q2"
SELECT QUARTER('2026-05-21');
```

Result:

```text id="q3"
2
```

---

## How it works

A year is divided into 4 quarters:

| Quarter | Months    |
| ------- | --------- |
| 1       | Jan – Mar |
| 2       | Apr – Jun |
| 3       | Jul – Sep |
| 4       | Oct – Dec |

So **May = Quarter 2**

---

## Important points

* Returns value from `1` to `4`
* Works with `DATE`, `DATETIME`, `TIMESTAMP`
* If value is `NULL`, result is `NULL`

---
