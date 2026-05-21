# ⏱️ `TIMEDIFF()`

Returns the difference between two time or datetime values

**Syntax**

```sql id="t1"
SELECT TIMEDIFF(time1, time2);
```

---

**Example**

```sql id="t2"
SELECT TIMEDIFF('15:45:30', '14:30:00');
```

Result:

```text id="t3"
01:15:30
```

---

## Important points

* Returns result in **HH:MM:SS format**
* Works with `TIME` and `DATETIME`
* Order matters (first - second)
* If value is `NULL`, result is `NULL`

---