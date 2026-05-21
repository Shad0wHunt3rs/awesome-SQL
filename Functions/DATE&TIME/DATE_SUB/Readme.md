# `DATE_SUB()`

Subtracts a specific time interval from a date

**Syntax**

```sql id="ds1"
SELECT DATE_SUB(date, INTERVAL value unit);
```

---

**Subtract days**

```sql id="ds2"
SELECT DATE_SUB('2026-05-21', INTERVAL 5 DAY);
```

Result:

```text id="ds3"
2026-05-16
```

---

**Subtract months**

```sql id="ds4"
SELECT DATE_SUB('2026-05-21', INTERVAL 2 MONTH);
```

Result:

```text id="ds5"
2026-03-21
```

---

**Subtract years**

```sql id="ds6"
SELECT DATE_SUB('2026-05-21', INTERVAL 1 YEAR);
```

Result:

```text id="ds7"
2025-05-21
```

---

## Important points

* Used to move backward in time
* Works with `DAY`, `MONTH`, `YEAR`, `HOUR`, etc.
* If date is `NULL`, result is `NULL`

---