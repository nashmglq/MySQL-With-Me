# Subqueries in MySQL

## 🔹 What is a Subquery?
A subquery is a query nested inside another query. It can be used to retrieve data that will be used in the main query.

## 🔹 Types of Subqueries
Subqueries can be categorized based on their placement and behavior:

### 1️⃣ **Scalar Subquery**
Returns a single value and can be used in SELECT, WHERE, or HAVING clauses.

```sql
SELECT name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

### 2️⃣ **Column Subquery**
Returns a single column of values and can be used with `IN`, `NOT IN`, or comparison operators.

```sql
SELECT name
FROM employees
WHERE department_id IN (SELECT department_id FROM departments WHERE location = 'New York');
```

### 3️⃣ **Row Subquery**
Returns multiple columns but only one row and is used with `=`, `<`, `>`, etc.

```sql
SELECT name, salary
FROM employees
WHERE (department_id, job_id) = (SELECT department_id, job_id FROM employees WHERE name = 'John Doe');
```

### 4️⃣ **Table Subquery**
Returns multiple rows and columns, often used in the FROM clause.

```sql
SELECT avg_salary
FROM (SELECT department_id, AVG(salary) AS avg_salary FROM employees GROUP BY department_id) AS dept_avg
WHERE avg_salary > 50000;
```

## 🔹 Subqueries in Different Clauses

### 📌 **Subquery in SELECT Clause**

```sql
SELECT name, (SELECT department_name FROM departments WHERE department_id = employees.department_id) AS department_name
FROM employees;
```

### 📌 **Subquery in FROM Clause (Derived Table)**

```sql
SELECT department_id, avg_salary FROM (SELECT department_id, AVG(salary) AS avg_salary FROM employees GROUP BY department_id) AS dept_avg;
```

### 📌 **Subquery in WHERE Clause**

```sql
SELECT name, salary FROM employees WHERE salary > (SELECT AVG(salary) FROM employees);
```

### 📌 **Subquery in HAVING Clause**

```sql
SELECT department_id, AVG(salary) AS avg_salary FROM employees GROUP BY department_id HAVING AVG(salary) > (SELECT AVG(salary) FROM employees);
```

## 🔹 Subquery Best Practices
- Use indexes on columns involved in subqueries for better performance.
- Avoid unnecessary subqueries; sometimes, joins are more efficient.
- Ensure subqueries return only the expected number of rows.
- Use `EXISTS` for better performance when checking for existence rather than `IN`.

## 🔹 `EXISTS` vs. `IN` in Subqueries

### ✅ `EXISTS` (Better for large datasets)
```sql
SELECT name FROM employees e WHERE EXISTS (SELECT 1 FROM departments d WHERE d.department_id = e.department_id);
```

### ❌ `IN` (Slower for large datasets)
```sql
SELECT name FROM employees WHERE department_id IN (SELECT department_id FROM departments);
```

---

This covers all key aspects of MySQL subqueries. Let me know if you need further details or examples! 🚀



## 🔹 EXAMPLE 
```sql
SELECT e.employee_id, e.name, e.department, e.salary
FROM employee e
WHERE e.salary > (
    SELECT AVG(salary)
    FROM employee
    -- TO GET each department
    -- parang kung saan ung department naten ay = sa department from main query
    WHERE department = e.department
);
```

