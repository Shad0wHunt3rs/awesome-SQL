# CAST()

`CAST()` converts a value from one data type to another.

It is the **ANSI SQL standard** way of type conversion, so it is supported by most database systems such as MySQL, PostgreSQL, SQL Server, and Oracle.


**Syntax**

```sql id="cast01"
CAST(expression AS datatype)
```

* **expression** = value to convert
* **datatype** = target data type

---

**Examples**

**String to Integer**

```sql id="cast02"
SELECT CAST('123' AS UNSIGNED);
```

Output:

```text id="cast03"
123
```

---

**Integer to String**

```sql id="cast04"
SELECT CAST(123 AS CHAR);
```

Output:

```text id="cast05"
'123'
```

---

**String to Decimal**

```sql id="cast06"
SELECT CAST('123.45' AS DECIMAL(10,2));
```

Output:

```text id="cast07"
123.45
```

---

**String to Date**

```sql id="cast08"
SELECT CAST('2026-05-31' AS DATE);
```

Output:

```text id="cast09"
2026-05-31
```

---

**String to Datetime**

```sql id="cast10"
SELECT CAST('2026-05-31 14:30:45' AS DATETIME);
```

Output:

```text id="cast11"
2026-05-31 14:30:45
```

---

**String to Time**

```sql id="cast12"
SELECT CAST('14:30:45' AS TIME);
```

Output:

```text id="cast13"
14:30:45
```

---

# Common Data Types Used with CAST()

| Data Type    | Purpose                     |
| ------------ | --------------------------- |
| CHAR         | Convert to string           |
| BINARY       | Convert to binary string    |
| DATE         | Convert to date             |
| TIME         | Convert to time             |
| DATETIME     | Convert to datetime         |
| DECIMAL(M,D) | Convert to decimal          |
| SIGNED       | Convert to signed integer   |
| UNSIGNED     | Convert to unsigned integer |
| JSON         | Convert to JSON             |

---

## Numeric Conversions

**Convert String to Number**

```sql id="cast14"
SELECT CAST('500' AS UNSIGNED);
```

Output:

```text id="cast15"
500
```

---

**Convert Decimal String**

```sql id="cast16"
SELECT CAST('99.99' AS DECIMAL(5,2));
```

Output:

```text id="cast17"
99.99
```

---

**Convert Negative Number**

```sql id="cast18"
SELECT CAST('-50' AS SIGNED);
```

Output:

```text id="cast19"
-50
```

---

## Character Conversions

**Number to Character**

```sql id="cast20"
SELECT CAST(500 AS CHAR);
```

Output:

```text id="cast21"
'500'
```

---

**Decimal to Character**

```sql id="cast22"
SELECT CAST(99.99 AS CHAR);
```

Output:

```text id="cast23"
'99.99'
```

---

## Date Conversions

**String to Date**

```sql id="cast24"
SELECT CAST('2026-05-31' AS DATE);
```

Output:

```text id="cast25"
2026-05-31
```

---

**String to Time**

```sql id="cast26"
SELECT CAST('15:45:20' AS TIME);
```

Output:

```text id="cast27"
15:45:20
```

---

**String to Datetime**

```sql id="cast28"
SELECT CAST('2026-05-31 15:45:20' AS DATETIME);
```

Output:

```text id="cast29"
2026-05-31 15:45:20
```

---

--

## Invalid Conversions

**Text to Number**

```sql id="cast39"
SELECT CAST('ABC' AS UNSIGNED);
```

Output:

```text id="cast40"
0
```

MySQL may generate a warning.

---

**Decimal to Integer**

```sql id="cast41"
SELECT CAST('123.99' AS UNSIGNED);
```

Output:

```text id="cast42"
123
```

Fractional part is removed.

---

# CAST() vs STR_TO_DATE()

### CAST()

Works when the string is already in MySQL date format:

```sql id="cast43"
SELECT CAST('2026-05-31' AS DATE);
```

---

### STR_TO_DATE()

Works with custom formats:

```sql id="cast44"
SELECT STR_TO_DATE('31/05/2026',
                   '%d/%m/%Y');
```

Output:

```text id="cast45"
2026-05-31
```

Use `STR_TO_DATE()` when the input format is not already `YYYY-MM-DD`.

---

# CAST() vs CONVERT()

**CAST**

```sql id="cast46"
SELECT CAST('123' AS UNSIGNED);
```

**CONVERT**

```sql id="cast47"
SELECT CONVERT('123', UNSIGNED);
```

Both return:

```text id="cast48"
123
```

Difference:

| Feature                  | CAST() | CONVERT() |
| ------------------------ | ------ | --------- |
| ANSI SQL Standard        | Yes    | No        |
| Data Type Conversion     | Yes    | Yes       |
| Character Set Conversion | No     | Yes       |

>[!NOTE]
> ANSI SQL refers to the standardized version of Structured Query Language (SQL) defined by the American National Standards Institute (ANSI). Its main purpose is to establish a uniform set of rules, syntax, and commands for managing relational databases across different vendor platforms (e.g., MySQL, PostgreSQL, Oracle, SQL Server).


---

**When to Use CAST()**

Use `CAST()` when:

* Converting strings to numbers
* Converting numbers to strings
* Converting strings to dates/times
* Performing numeric comparisons
* Writing portable SQL code

---
