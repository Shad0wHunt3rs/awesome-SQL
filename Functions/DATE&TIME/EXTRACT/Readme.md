# EXTRACT

`EXTRACT()` is an SQL date/time function used to extract a specific part from a date, time, or datetime value.

**Syntax:**

```sql
EXTRACT(part FROM date_value)
```

**Examples:**

```sql
SELECT EXTRACT(YEAR FROM '2026-05-31');
-- 2026

SELECT EXTRACT(MONTH FROM '2026-05-31');
-- 5

SELECT EXTRACT(HOUR FROM '14:30:45');
-- 14
```

**Common parts:**

* `YEAR`
* `MONTH`
* `DAY`
* `HOUR`
* `MINUTE`
* `SECOND`
* `WEEK`
* `QUARTER`
