# NOW 

In SQL, **`NOW()`** is a date & time function that returns the **current date and time** of the server.

**Syntax**

```sql
SELECT NOW();
```

**Example Output**

```text
2026-05-21 15:30:45
```

---

## Important points

* Includes **date + time**
* Based on **server time**
* Value changes every time you run it
* Often used in logs, timestamps, and records

---

**Example** 

```sql
INSERT INTO users (name, created_at)
VALUES ('Ali', NOW());
```

This stores the exact time the record was created.

---
