# Common Table Expressions (CTEs) in MySQL

## 🔹 What is a CTE?
A **Common Table Expression (CTE)** is a temporary result set that can be referenced within a `SELECT`, `INSERT`, `UPDATE`, or `DELETE` statement. It improves query readability and reusability.

CTEs are defined using the `WITH` clause.

## 🔹 Syntax of CTE in MySQL
```sql
WITH cte_name AS (
    SELECT column1, column2
    FROM table_name
    WHERE condition
)
SELECT * FROM cte_name;
```

## 🔹 Benefits of Using CTEs
- Improves **readability** of complex queries.
- Allows **recursive queries**.
- Simplifies **nested subqueries**.
- Enhances **code maintainability**.

## 🔹 Types of CTEs

### 1️⃣ Non-Recursive CTE
A standard CTE that does not reference itself.

```sql
WITH EmployeeCTE AS (
    SELECT id, name, salary
    FROM employees
    WHERE salary > 50000
)
SELECT * FROM EmployeeCTE;
```

### 2️⃣ Recursive CTE
A CTE that references itself, commonly used for hierarchical data like organizational charts or category trees.

```sql
WITH RECURSIVE EmployeeHierarchy AS (
    -- Base case
    SELECT id, name, manager_id, 1 AS level
    FROM employees
    WHERE manager_id IS NULL
    
    UNION ALL
    
    -- Recursive case
    SELECT e.id, e.name, e.manager_id, eh.level + 1
    FROM employees e
    INNER JOIN EmployeeHierarchy eh
    ON e.manager_id = eh.id
)
SELECT * FROM EmployeeHierarchy;
```

## 🔹 CTE vs. Subquery
| Feature | CTE | Subquery |
|---------|-----|---------|
| Readability | High | Low |
| Reusability | Can be referenced multiple times | Not reusable |
| Performance | Better for complex queries | Can be inefficient |

## 🔹 When to Use CTEs?
- When dealing with **hierarchical data**.
- To improve **query readability**.
- When a **subquery** is repeated multiple times.

---
✅ **CTEs make SQL queries cleaner, structured, and more efficient!** 🚀

