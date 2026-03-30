# **DROP Command in SQL**

The **DROP** command is part of **DDL (Data Definition Language)**.
It is used to **permanently delete database objects**, such as:

* Tables
* Databases
* Views
* Indexes
* Schemas

> ⚠️ **Warning:** Once dropped, the object and its data **cannot be recovered** (unless you have a backup).


## **Drop a Table**

Deletes the table **and all its data** permanently.

```sql
DROP TABLE table_name;
```

**Example:**

```sql
DROP TABLE person;
```

* Table `person` is removed completely.
* All rows and structure are deleted.
* Cannot be rolled back.

---

## **Drop a Database**

Deletes the **entire database** and all its tables.

```sql
DROP DATABASE database_name;
```

**Example:**

```sql
DROP DATABASE school;
```

---

## **Drop a View**

Deletes a **view** without affecting underlying tables.

```sql
DROP VIEW view_name;
```

**Example:**

```sql
DROP VIEW active_students;
```

---

## **Drop an Index**

Deletes an **index** to stop optimizing searches.

```sql
DROP INDEX index_name ON table_name;
```

**Example:**

```sql
DROP INDEX idx_name ON students;
```

---

## **Key Points**

1. **Permanent deletion** – auto-committed in most databases.
2. **Data is lost** for tables.
3. For partial data removal, use **DELETE** or **TRUNCATE** instead of DROP.
4. Useful when removing **obsolete tables, databases, or indexes**.

---