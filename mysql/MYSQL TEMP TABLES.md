# Temporary Tables in MySQL

## 🔹 What is a Temporary Table?
A **Temporary Table** in MySQL is a table that exists only for the duration of a session. It is automatically dropped when the session ends, making it useful for storing intermediate results without affecting the main database.

## 🔹 Syntax for Creating a Temporary Table
```sql
CREATE TEMPORARY TABLE temp_table_name (
    column1 datatype,
    column2 datatype,
    ...
);
```

## 🔹 Example of Temporary Table Usage
```sql
CREATE TEMPORARY TABLE TempEmployees (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    salary DECIMAL(10,2)
);

INSERT INTO TempEmployees (id, name, salary)
VALUES (1, 'John Doe', 60000), (2, 'Jane Smith', 75000);

SELECT * FROM TempEmployees;
```

## 🔹 Key Features of Temporary Tables
- **Session-Specific**: The table is automatically dropped when the session ends.
- **Same-Name Tables**: Different sessions can create temporary tables with the same name without conflicts.
- **No Persistence**: Data in a temporary table is not stored permanently.

## 🔹 Dropping a Temporary Table
To manually drop a temporary table before the session ends:
```sql
DROP TEMPORARY TABLE IF EXISTS temp_table_name;
```

## 🔹 Using Temporary Tables with Joins
Temporary tables can be used to store intermediate query results for further processing.
```sql
CREATE TEMPORARY TABLE TempOrders AS
SELECT customer_id, COUNT(*) AS order_count
FROM orders
GROUP BY customer_id;

SELECT c.customer_name, t.order_count
FROM customers c
JOIN TempOrders t ON c.customer_id = t.customer_id;
```

## 🔹 Temporary Tables vs. Regular Tables
| Feature | Temporary Table | Regular Table |
|---------|----------------|--------------|
| Persistence | Exists only during session | Exists permanently |
| Accessibility | Available only to the session that created it | Accessible to all users |
| Storage | Stored in memory or temporary storage | Stored on disk |

## 🔹 When to Use Temporary Tables?
- **Complex Queries**: Store intermediate results to improve query performance.
- **Data Processing**: Useful for breaking down large operations into smaller, manageable steps.
- **Session-Specific Calculations**: Keep temporary data isolated from other users.

---
✅ **Temporary tables are a great way to manage temporary data efficiently in MySQL!** 🚀

