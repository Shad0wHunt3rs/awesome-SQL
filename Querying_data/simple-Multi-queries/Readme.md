# **Basic Multi-Query Explained**

Simply put: **Running multiple SELECT statements one after another in a single go.**

```sql
SELECT * FROM table1;
SELECT * FROM table2;
SELECT * FROM table3;
```

**How it works:**

- Each statement ends with a semicolon `;`
- The database executes them **in order** (top to bottom)
- You get **multiple result sets** back (one for each SELECT)

**Example:**

```sql
SELECT * FROM customers;
SELECT * FROM orders;
```

**What happens:**

1. First query runs → returns all customers
2. Second query runs → returns all orders
3. Both results come back together


**Why use it:**

- **Convenience** - Run multiple queries at once instead of one by one
- **Debugging** - Quickly view several tables
- **Batch operations** - Get all data you need in one round trip

### **Important:**

- Each SELECT is **independent** (they don't affect each other)
- Order matters - they run exactly as written
- Most database tools show results in separate tabs/panels
