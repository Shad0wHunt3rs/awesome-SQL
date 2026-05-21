# `TIME_FORMAT()`

Formats a time value into a custom format

**Syntax**

```sql id="tf1"
SELECT TIME_FORMAT(time, format);
```

---

**Example**

```sql id="tf2"
SELECT TIME_FORMAT('15:45:30', '%H:%i');
```

Result:

```text id="tf3"
15:45
```

---

## Format symbols

| Symbol | Meaning      | Example |
| ------ | ------------ | ------- |
| `%H`   | Hour (00–23) | 15      |
| `%h`   | Hour (01–12) | 03      |
| `%i`   | Minutes      | 45      |
| `%s`   | Seconds      | 30      |
| `%p`   | AM/PM        | PM      |

---

**AM/PM format**

```sql id="tf4"
SELECT TIME_FORMAT('15:45:30', '%h:%i:%s %p');
```

Result:

```text id="tf5"
03:45:30 PM
```

---

## Important points

* Works only with **TIME values**
* Does NOT change stored data (only display format)
* If value is `NULL`, result is `NULL`

---
