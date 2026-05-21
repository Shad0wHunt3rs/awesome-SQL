# `CURRENT_TIMESTAMP()`

Returns the current date and time

**Syntax**

```sql id="c1"
SELECT CURRENT_TIMESTAMP();
```

**Example Output**

```text id="c2"
2026-05-21 15:50:10
```

---

## Important points

* Same result as `NOW()` in MySQL
* Returns **date + time**
* Based on server system time
* Commonly used for timestamps in records

---

**Example**

```sql id="c3"
INSERT INTO orders (customer_name, created_at)
VALUES ('Ali', CURRENT_TIMESTAMP());
```

---