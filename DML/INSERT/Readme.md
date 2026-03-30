
# **INSERT**

`INSERT` is a **DML (Data Manipulation Language)** command used to **add new rows** into a table.

```sql
INSERT INTO table_name (column1, column2, column3)
VALUES (value1, value2, value3);
```

This inserts **one new row**.

## **Inserting Into All Columns**

If you want to insert values for *every column* (in correct order):

```sql
INSERT INTO table_name
VALUES (value1, value2, value3, ...);
```

Example:

```sql
INSERT INTO students
VALUES (1, 'Ali', '10th Grade');
```

## **Insert Into Selected Columns Only**

If some columns have **default values** or allow **NULL**, you can insert into specific columns:

```sql
INSERT INTO students (id, name)
VALUES (1, 'Ali');
```

The missing column(s) will get:

* DEFAULT value
* or NULL
  (depending on table design)



## **Insert Multiple Rows at Once**

```sql
INSERT INTO students (id, name, class)
VALUES
(1, 'Ali', '10th'),
(2, 'Sara', '9th'),
(3, 'Bilal', '8th');
```

This is faster than inserting row by row.


## **INSERT Using SELECT (Copy Data From Another Table)**

```sql
INSERT INTO new_students (id, name, class)
SELECT id, name, class
FROM students
WHERE class = '10th';
```

This inserts data selected from another table.

---

## **Default Values with INSERT**

If a column has a default:

```sql
INSERT INTO students (name)
VALUES ('Ali');
```

The other columns automatically get their **DEFAULT** values.

If you want to use default manually:

```sql
INSERT INTO students (id, name, class)
VALUES (DEFAULT, 'Ali', DEFAULT);
```

---

## **Transaction Behavior (Important)**

Since `INSERT` is **DML**, it can be rolled back:

```sql
START TRANSACTION;

INSERT INTO students VALUES (1, 'Ali', '10th');

ROLLBACK;   -- The inserted row will be removed
```

`COMMIT` makes it permanent.

---

## **Common Errors in INSERT**

- **Not providing required columns** : If a column is NOT NULL and you don’t give a value → error.

- **Wrong data type** : INSERT INTO students (id) VALUES ('abc'); -- Error because id expects a number.

- **Duplicate primary key** : 

If `id` is a primary key:

```sql
INSERT INTO students VALUES (1, 'Ali', '10th');
INSERT INTO students VALUES (1, 'Sara', '9th');   -- error
```
