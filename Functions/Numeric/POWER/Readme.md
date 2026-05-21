# `POWER()`

`POWER()` is a numeric function used to raise a number to a specified exponent (power).

**Syntax**

```sql id="p1"
POWER(base, exponent)
```

* `base` → number to multiply
* `exponent` → how many times to multiply it

---

**Example**

```sql id="p2"
SELECT POWER(2, 3);
```

Result:

```id="p3"
8
```

Explanation:

```id="p4"
2 × 2 × 2 = 8
```

---


## Decimal example

```sql id="p7"
SELECT POWER(2.5, 2);
```

Result:

```id="p8"
6.25
```

---

## Power of zero

```sql id="p9"
SELECT POWER(10, 0);
```

Result:

```id="p10"
1
```

Any non-zero number raised to power `0` equals `1`.

---

## Negative exponent

```sql id="p11"
SELECT POWER(2, -2);
```

Result:

```id="p12"
0.25
```

Explanation:

```id="p13"
1 / (2 × 2)
```

---

## NULL behavior

```sql id="p15"
SELECT POWER(NULL, 2);
```

Result:

```id="p16"
NULL
```

---

## Important notes

| Expression      | Meaning          |
| --------------- | ---------------- |
| `POWER(2, 3)`   | `2³`             |
| `POWER(5, 2)`   | `5²`             |
| `POWER(9, 0.5)` | square root of 9 |

---