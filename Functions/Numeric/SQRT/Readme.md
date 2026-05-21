# `SQRT()`

`SQRT()` is a numeric function used to find the **square root** of a number.

**Syntax**

```sql id="s1"
SQRT(number)
```

---

**Example**

```sql id="s2"
SELECT SQRT(25);
```

Result:

```id="s3"
5
```

because:

```id="s4"
5 × 5 = 25
```

---

## Decimal result

```sql id="s7"
SELECT SQRT(2);
```

Result:

```id="s8"
1.414213...
```

---

## Important rules

**1. Negative numbers**

```sql id="s10"
SELECT SQRT(-9);
```

Result:

* Usually `NULL` or error (depends on database)

Because square root of negative numbers is not real in standard SQL.


**2. Zero**

```sql id="s11"
SELECT SQRT(0);
```

Result:

```id="s12"
0
```

**3. NULL**

```sql id="s13"
SELECT SQRT(NULL);
```

Result:

```id="s14"
NULL
```

---