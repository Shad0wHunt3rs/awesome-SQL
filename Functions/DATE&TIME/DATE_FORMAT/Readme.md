# `DATE_FORMAT()`

Formats a date or datetime into a custom readable format

**Syntax**

```sql id="df1"
SELECT DATE_FORMAT(date, format);
```

---

**Example**

```sql id="df2"
SELECT DATE_FORMAT('2026-05-21', '%d-%m-%Y');
```

Result:

```text id="df3"
21-05-2026
```

---

## Common format symbols

| Symbol | Meaning         | Example |
| ------ | --------------- | ------- |
| `%Y`   | Year (4 digits) | 2026    |
| `%y`   | Year (2 digits) | 26      |
| `%m`   | Month (01–12)   | 05      |
| `%d`   | Day (01–31)     | 21      |
| `%H`   | Hour (00–23)    | 15      |
| `%i`   | Minutes         | 45      |
| `%s`   | Seconds         | 30      |

---

## Example**

```sql id="df4"
SELECT DATE_FORMAT(NOW(), '%d/%m/%Y %H:%i:%s');
```

Result:

```text id="df5"
21/05/2026 15:45:30
```

---

## Important points

* Does NOT change actual data (only display format)
* Works with `DATE`, `DATETIME`, `TIMESTAMP`
* If value is `NULL`, result is `NULL`

---
