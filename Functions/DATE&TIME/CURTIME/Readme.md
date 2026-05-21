# `CURTIME()`

Returns the current time only (no date)

**Syntax**

```sql id="t1"
SELECT CURTIME();
```

**Example Output**

```text id="t2"
15:45:30
```

---

## Important points

* Returns **only time (HH:MM:SS)**
* Does NOT include date
* Based on server system time
* Updates every second when queried

---

**Example**

```sql id="t3"
INSERT INTO logs (message, log_time)
VALUES ('Login success', CURTIME());
```

---
