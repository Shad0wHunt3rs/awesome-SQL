# `RAND()`

`RAND()` is a numeric function used to generate a **random number between 0 and 1**.

**Syntax**

```sql id="r1"
RAND()
```

---

**Example**

```sql id="r2"
SELECT RAND();
```

Result (example):

```id="r3"
0.482917
```

Each time you run it, you get a different value.

---

## How it works

It generates a decimal like:

* 0.1234
* 0.9876
* 0.0451

Always in range:

```text id="r4"
0 ≤ RAND() < 1
```

---

## Generate random range values

**Example: 1 to 10**

```sql id="r5"
SELECT FLOOR(RAND() * 10) + 1;
```

---

## Using in table sorting

```sql id="r6"
SELECT *
FROM customers
ORDER BY RAND();
```

This returns rows in random order.

---

# Important notes

**1. Value changes every time**

```sql id="r7"
SELECT RAND();
```

Each execution gives a new number.


**2. Can be used with seed (MySQL)**

```sql id="r8"
SELECT RAND(10);
```

Same seed → same random sequence.

---
