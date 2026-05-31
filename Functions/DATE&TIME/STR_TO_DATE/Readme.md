# STR_TO_DATE

`STR_TO_DATE()` converts a string into a DATE, TIME, or DATETIME value using a specified format.

**Syntax:**

```sql id="strtodate1"
STR_TO_DATE(string, format)
```

**Example:**

```sql id="strtodate2"
SELECT STR_TO_DATE('31-05-2026', '%d-%m-%Y');
```

**Output:**

```text
2026-05-31
```

**Another example:**

```sql id="strtodate3"
SELECT STR_TO_DATE('31/05/2026 14:30:45', '%d/%m/%Y %H:%i:%s');
```

**Common format specifiers:**

* `%Y` → 4-digit year
* `%m` → month (01–12)
* `%d` → day (01–31)
* `%H` → hour (00–23)
* `%i` → minutes
* `%s` → seconds

