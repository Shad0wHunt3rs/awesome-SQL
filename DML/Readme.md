# **DML**

**DML (Data Manipulation Language)** is a subset of SQL used to **manipulate data stored in tables**.
It allows you to **insert, update, delete, and retrieve rows**.

* **DML affects data only**, not the table structure (columns, constraints, etc.).
* Changes made by DML commands can usually be **rolled back** using transactions.

<img src="../introduction/Types_of_SQL_commands/types1.png" width="400">

<br>
<br>

## **DML Commands**

- **[INSERT](./INSERT/Readme.md)**
- **[UPDATE](./UPDATE/Readme.md)**
- **[DELETE]()**
- **[SELECT]()**


## **Key Features of DML**

| Feature    | Description                                                     |
| ---------- | --------------------------------------------------------------- |
| Data Level | Works on **rows** of a table.                                   |
| Rollback   | Changes can be undone using transactions (`COMMIT`/`ROLLBACK`). |
| Dependency | Cannot change **structure** (use DDL for that).                 |
| Scope      | Only affects data, not metadata or table definition.            |

---
