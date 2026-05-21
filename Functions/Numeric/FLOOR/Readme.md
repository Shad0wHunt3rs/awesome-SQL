# `FLOOR()`

`FLOOR()` is a numeric function used to round a number **downward** to the nearest integer.

**Syntax**

```sql id="f1"
FLOOR(number)
```

---

**Example**

```sql id="f2"
SELECT FLOOR(4.9);
```

Result:

```id="f3"
4
```

because the number is rounded downward.

---

## Whole number case

```sql id="f6"
SELECT FLOOR(10);
```

Result:

```id="f7"
10
```

Already an integer, so no change.

---

## Negative numbers

```sql id="f8"
SELECT FLOOR(-4.2);
```

Result:

```id="f9"
-5
```

Why?
Because `-5` is mathematically smaller than `-4.2`.

---

## Important concept

`FLOOR()` always moves toward the smaller integer.

| Number | Result |
| ------ | ------ |
| `4.1`  | `4`    |
| `4.9`  | `4`    |
| `-4.1` | `-5`   |
| `-4.9` | `-5`   |


---

## NULL behavior

```sql id="f11"
SELECT FLOOR(NULL);
```

Result:

```id="f12"
NULL
```

---