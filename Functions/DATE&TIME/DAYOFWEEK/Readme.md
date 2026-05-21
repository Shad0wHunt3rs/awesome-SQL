# `DAYOFWEEK()`

Returns the weekday number from a date

**Syntax**

```sql id="dw1"
SELECT DAYOFWEEK(date);
```

---

## Example

```sql id="dw2"
SELECT DAYOFWEEK('2026-05-21');
```

Result:

```text id="dw3"
5
```

---

## Weekday Numbers

| Number | Day       |
| ------ | --------- |
| 1      | Sunday    |
| 2      | Monday    |
| 3      | Tuesday   |
| 4      | Wednesday |
| 5      | Thursday  |
| 6      | Friday    |
| 7      | Saturday  |

---

## Important points

* Returns values from `1` to `7`
* Works with `DATE`, `DATETIME`, `TIMESTAMP`
* If value is `NULL`, result is `NULL`

---