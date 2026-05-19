# EXCEPT

`EXCEPT` is a SQL set operator used to return:

> rows from the **first query** that do NOT exist in the second query.


<img src="./1.png" width="500">

<br>
<br>


<img src="./2.png" width="300">

Meaning:

> “Give me rows in A that are NOT in B”


**Basic Syntax**

```sql id="v7k2qp"
SELECT column1, column2
FROM table1

EXCEPT

SELECT column1, column2
FROM table2;
```

---

## Important Rule

`EXCEPT` automatically removes duplicates.

So it behaves more like:

```text
DISTINCT(A - B)
```

---

## Performance Notes

`EXCEPT` internally:

* sorts data
* compares rows
* removes duplicates

So:

> slower than simple filtering sometimes

---

## MYSQL alternative 

EXCEPT does NOT work in MySQL.

so its alternative is `NOT EXISTS`

here how it works 


```sql
SELECT 
    c.firstname, c.lastname
FROM
    salesdb.customers AS c
WHERE
    NOT EXISTS( SELECT 
            1
        FROM
            salesdb.employees AS e
        WHERE
            c.firstname = e.firstname
                AND c.lastname = e.lastname);
```

“If no matching row exists in the subquery, show the row.”

here `SELECT 1` is just a dummy value. It means: “If a matching row exists, return the number 1.”

so the where result becomes

```text
EXISTS      → found
NOT EXISTS  → not found
```


we can also solve this problem by using `NOT IN`

look similar, but they work differently internally.


```sql
SELECT 
    firstname,
    lastname
FROM salesdb.customers
WHERE (firstname, lastname) NOT IN (
    SELECT firstname, lastname
    FROM salesdb.employees
);
```


but there is some thing wrong with it as if the table contains `NULL` then NOT IN may return no rows unexpectedly.


heres the output of both 

**NOT EXISTS**

<img src="./3.png" width="400">

**NOT IN**

<img src="./4.png" width="400">

<br>
<br>


the reason behind this is that `NOT IN` checks internally that when it check for `NULL` it does know if it is NOT true or false. so it becomes unknown, so the row is NOT shown.

In SQL: NULL is not a normal value

It means: unknown / missing value

So comparisons with NULL do not behave normally.

so use `NOT EXISTS` here in this
