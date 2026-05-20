# `LOWER()` and `UPPER()`

These are **string functions** used to change the letter case of text.

* `LOWER()` → converts text to lowercase
* `UPPER()` → converts text to uppercase

---

## `LOWER()`

> `LOWER()` converts all characters in a string to lowercase.

**Syntax**

```sql id="l1"
LOWER(string)
```

---

## `UPPER()`

> `UPPER()` converts all characters in a string to uppercase.

**Syntax**

```sql id="u1"
UPPER(string)
```

---


---

### Important Notes

- They do not modify the actual table data
- They work only on strings/text
- Numbers are unaffected
- If the value is NULL, then LOWER() and UPPER() also return NULL.

---
