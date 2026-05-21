# `DATE_ADD()`

Adds a specific time interval to a date

**Syntax**

```sql id="d1"
SELECT DATE_ADD(date, INTERVAL value unit);
```

<br>

>[!NOTE]
> INTERVAL is a keyword used to specify a time period or duration when working with dates.

---

**Add days**

```sql id="d2"
SELECT DATE_ADD('2026-05-21', INTERVAL 5 DAY);
```

Result:

```text id="d3"
2026-05-26
```

---

**Add months**

```sql id="d4"
SELECT DATE_ADD('2026-05-21', INTERVAL 2 MONTH);
```

Result:

```text id="d5"
2026-07-21
```

---

**Add years**

```sql id="d6"
SELECT DATE_ADD('2026-05-21', INTERVAL 1 YEAR);
```

Result:

```text id="d7"
2027-05-21
```

---

## Important points

* Used to move forward in time
* Works with `DAY`, `MONTH`, `YEAR`, `HOUR`, `MINUTE`, `SECOND`
* If input date is `NULL`, result is `NULL`

---
