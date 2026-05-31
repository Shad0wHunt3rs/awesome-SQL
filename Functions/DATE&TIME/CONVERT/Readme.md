# CONVERT()

`CONVERT()` is used to convert a value from one data type to another or to convert a string from one character set to another.

**Syntax 1: Data Type Conversion**

```sql id="conv01"
CONVERT(expression, datatype)
```

**Example**

```sql id="conv02"
SELECT CONVERT('123', UNSIGNED);
```

Output:

```text
123
```

---

**Syntax 2: Character Set Conversion**

```sql id="conv03"
CONVERT(string USING charset)
```

**Example**

```sql id="conv04"
SELECT CONVERT('Hello' USING utf8mb4);
```

Converts the string to the `utf8mb4` character set.

---

## Data Type Conversion Examples

### String to Integer

```sql id="conv05"
SELECT CONVERT('100', UNSIGNED);
```

Output:

```text
100
```

---

### String to Signed Integer

```sql id="conv06"
SELECT CONVERT('-100', SIGNED);
```

Output:

```text
-100
```

---

### Integer to String

```sql id="conv07"
SELECT CONVERT(100, CHAR);
```

Output:

```text
'100'
```

---

### String to Decimal

```sql id="conv08"
SELECT CONVERT('123.45', DECIMAL(10,2));
```

Output:

```text
123.45
```

---

### String to Date

```sql id="conv09"
SELECT CONVERT('2026-05-31', DATE);
```

Output:

```text
2026-05-31
```

---

### String to Datetime

```sql id="conv10"
SELECT CONVERT('2026-05-31 14:30:45', DATETIME);
```

Output:

```text
2026-05-31 14:30:45
```

---

### String to Time

```sql id="conv11"
SELECT CONVERT('14:30:45', TIME);
```

Output:

```text
14:30:45
```

---

## Common Data Types

| Type         | Description      |
| ------------ | ---------------- |
| CHAR         | String           |
| BINARY       | Binary string    |
| DATE         | Date             |
| TIME         | Time             |
| DATETIME     | Date and time    |
| DECIMAL(M,D) | Decimal number   |
| SIGNED       | Signed integer   |
| UNSIGNED     | Unsigned integer |
| JSON         | JSON value       |

---

### Character Set Conversion

MySQL stores text using character sets.

Examples:

* `utf8mb4`
* `latin1`
* `ascii`

---

### Convert Using UTF8MB4

```sql id="conv12"
SELECT CONVERT('Hello' USING utf8mb4);
```

---

### Convert Using ASCII

```sql id="conv13"
    SELECT CONVERT('Hello' USING ascii);
```

---

### Check Character Set

```sql id="conv14"
SELECT CHARSET(CONVERT('Hello' USING utf8mb4));
```

Output:

```text
utf8mb4
```

---

### Practical Uses

**Numeric Comparison**

Without conversion:

```sql id="conv15"
SELECT '100' > '20';
```

Result:

```text
0
```

String comparison is alphabetical.

With conversion:

```sql id="conv16"
SELECT CONVERT('100', UNSIGNED) >
       CONVERT('20', UNSIGNED);
```

Result:

```text
1
```

---

**Calculations**

```sql id="conv17"
SELECT CONVERT('50', UNSIGNED) + 25;
```

Output:

```text
75
```

---

**Formatting Data**

```sql id="conv18"
SELECT CONCAT('ID: ', CONVERT(100, CHAR));
```

Output:

```text
ID: 100
```

---
