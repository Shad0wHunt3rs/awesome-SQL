# `MOD()`

`MOD()` is a numeric function used to find the **remainder** after division.

**Syntax**

```sql id="m1"
MOD(number, divisor)
```

* `number` → value to divide
* `divisor` → number used for division

---

**Example**

```sql id="m2"
SELECT MOD(10, 3);
```

Result:

```id="m3"
1
```

Explanation:

```id="m4"
10 ÷ 3 = 3 remainder 1
```

---

# MOD operator alternative

In MySQL, `%` also works:

```sql id="m10"
SELECT 10 % 3;
```

Result:

```id="m11"
1
```

---

# Negative numbers

```sql id="m12"
SELECT MOD(-10, 3);
```

Result may depend on SQL database rules.

---

# NULL behavior

```sql id="m13"
SELECT MOD(NULL, 3);
```

Result:

```id="m14"
NULL
```

---

# Division by zero

```sql id="m15"
SELECT MOD(10, 0);
```

This causes an error or returns `NULL` depending on the DBMS.

---