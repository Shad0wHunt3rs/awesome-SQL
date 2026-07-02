# Location (Clauses) of Subqueries

A **subquery** can be placed in different parts of an SQL statement depending on its purpose. The location of the subquery determines how its result is used by the main (outer) query. The most common places where subqueries are used are:

* **[SELECT](./SELECT/Readme.md) clause** – Returns a value as part of the output.
* **[FROM](./FROM/Readme.md) clause** – Acts as a temporary table (derived table).
* **[JOIN](./JOIN/Readme.md) clause** – Joins the main query with the result of another query.
* **[WHERE](./WHERE/Readme.md) clause** – Filters rows based on the result of a subquery using comparison or logical operators.

The **`WHERE` clause** is the most common place for subqueries. Here, subqueries are used with:

* **Comparison Operators:** `=`, `>`, `<`, `>=`, `<=`, `<>`
* **Logical Operators:** `IN`, `ANY`, `ALL`, `EXISTS`

Each location serves a different purpose, allowing SQL queries to become more flexible, readable, and powerful.
