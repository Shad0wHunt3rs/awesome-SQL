# **CREATE Command in SQL**

The **CREATE** command is part of **DDL (Data Definition Language)**.
It is used to **create new database objects**, such as:

* Databases
* Tables
* Views
* Indexes
* Schemas
* Functions / Procedures (depends on SQL dialect)

When you run a `CREATE` command, the structure is created **permanently** because DDL is **auto-committed**.

---

# **1. CREATE DATABASE**

Used to create a **new database**.

```sql
CREATE DATABASE database_name;
```

---

# **2. CREATE TABLE**

Used to create a **new table** with columns and data types.


```sql
CREATE TABLE table_name (
    column_name datatype constraints,
    column_name datatype constraints,
    ...
);
```

---

# **3. CREATE TABLE with Constraints**

You can add constraints like:

* **PRIMARY KEY**
* **FOREIGN KEY**
* **UNIQUE**
* **NOT NULL**
* **CHECK**
* **DEFAULT**

### Example:

```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    salary DECIMAL(10,2) CHECK (salary > 0),
    department VARCHAR(50) DEFAULT 'General'
);
```

---

# **4. CREATE TABLE LIKE another table (copy structure only)**

```sql
CREATE TABLE new_table LIKE old_table;
```

This copies structure but **not** data.

---

# **5. CREATE TABLE AS SELECT (CTAS)**

Copies both structure **and** data.

```sql
CREATE TABLE backup_students AS
SELECT * FROM students;
```

---

# **6. CREATE VIEW**

A view is a **virtual table**.

```sql
CREATE VIEW active_students AS
SELECT name, age
FROM students
WHERE age > 18;
```

---

# **7. CREATE INDEX**

Used to speed up search queries.

```sql
CREATE INDEX idx_name
ON students (name);
```

---

# **8. CREATE SCHEMA**

Used to create a logical container (namespace).

```sql
CREATE SCHEMA sales;
```

---

## **Important Characteristics of CREATE**

1. **Auto-commit** → cannot rollback after creation.
2. **Defines structure** → sets the blueprint for tables.
3. **Mostly used by DBAs and developers**.
4. **Permanent unless dropped** (`DROP TABLE`, `DROP DATABASE`).
5. **Requires valid data types** (e.g., INT, VARCHAR, DATE).

---

### **Example**

Creating a full table with all constraints:

```sql
CREATE TABLE person (
    id INT NOT NULL,
    person_name VARCHAR(50) NOT NULL,
    birth_date DATE,
    phone VARCHAR(15) NOT NULL,
    CONSTRAINT pk_persons PRIMARY KEY (id)    
)
```

* This command **creates a table named `person`** with columns for id, name, birth date, and phone number.
* It also sets **`id` as the primary key** using the constraint `pk_persons`, ensuring each id is unique and not null.



>[!NOTE]
> `emp_id INT PRIMARY KEY` defines the primary key directly on the column and is used for simple single-column keys.
> `CONSTRAINT pk_employee PRIMARY KEY (emp_id)` defines it at the table level, lets you name the constraint, and is required for multi-column keys.

---

## **Summary**

| CREATE Object          | Purpose                |
| ---------------------- | ---------------------- |
| CREATE DATABASE        | Make a new database    |
| CREATE TABLE           | Make a new table       |
| CREATE VIEW            | Create a virtual table |
| CREATE INDEX           | Improve search speed   |
| CREATE SCHEMA          | Create a namespace     |
| CREATE TABLE AS SELECT | Copy table + data      |
| CREATE TABLE LIKE      | Copy only structure    |

---

