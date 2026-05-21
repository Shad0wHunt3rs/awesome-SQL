# `CEIL()` / `CEILING()`

`CEIL()` (or `CEILING()`) is a numeric function used to round a number **upward** to the nearest integer.

**Syntax**

```sql id="c1"
CEIL(number)
```

or

```sql id="c2"
CEILING(number)
```

Both work the same in many databases.

---

# Example 1

```sql id="c3"
SELECT CEIL(4.2);
```

Result:

```id="c4"
5
```

because the number is rounded upward.

---

## Whole number case

```sql id="c7"
SELECT CEIL(10);
```

Result:

```id="c8"
10
```

Already an integer, so no change.

---

## Negative numbers

```sql id="c9"
SELECT CEIL(-4.8);
```

Result:

```id="c10"
-4
```

Why?
Because `-4` is mathematically greater than `-4.8`.

---

## Important concept

`CEIL()` always moves toward the greater integer.

| Number | Result |
| ------ | ------ |
| `4.1`  | `5`    |
| `4.9`  | `5`    |
| `-4.1` | `-4`   |
| `-4.9` | `-4`   |

---


## NULL behavior

```sql id="c12"
SELECT CEIL(NULL);
```

Result:

```id="c13"
NULL
```

---

