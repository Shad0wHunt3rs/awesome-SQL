# `CURDATE()`

Returns the current date only (no time)

**Syntax**

```sql id="c1"
SELECT CURDATE();
```

**Example Output**

```text id="c2"
2026-05-21
```

---

## Important points

* Returns **only date (YYYY-MM-DD)**
* Does NOT include time
* Based on server system date
* Changes automatically every day

---

**Example**

```sql id="c3"
INSERT INTO orders (customer_name, order_date)
VALUES ('Ali', CURDATE());
```

This stores only the current date.

---