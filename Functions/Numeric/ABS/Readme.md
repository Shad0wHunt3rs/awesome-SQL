# `ABS()`

`ABS()` is a numeric function used to get the **absolute (positive) value** of a number.

> `ABS()` returns the non-negative value of a number by removing its sign.

**Syntax**

```sql id="a1"
ABS(number)
```

**How it works**

| Input | Output |
| ----- | ------ |
| `10`  | `10`   |
| `-10` | `10`   |
| `0`   | `0`    |

It removes only the negative sign.

---

## Important notes

**1. Works only on numeric values**

```sql id="a12"
ABS(number)
```

**2. `NULL` behavior**

```sql id="a13"
SELECT ABS(NULL);
```

Result:

```id="a14"
NULL
```

**3. Does not change actual table data**

It only changes query output unless used with `UPDATE`.

---

## Difference from negative sign

```sql id="a15"
SELECT -(-5);
```

also gives `5`, but `ABS()` is clearer and standard for absolute values.

---
