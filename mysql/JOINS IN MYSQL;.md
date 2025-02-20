# Joins in MySQL

## 1. INNER JOIN  
An **INNER JOIN** returns only the matching rows from both tables based on the given condition. If there is no match, the row is excluded.

### Syntax:
```sql
SELECT table1.column, table2.column
FROM table1
INNER JOIN table2
ON table1.col = table2.col;
```

### Example:
```sql
SELECT employees.name, departments.department_name
FROM employees
INNER JOIN departments
ON employees.department_id = departments.id;
```
This query returns employees who are assigned to a department.

---

## 2. LEFT JOIN  
A **LEFT JOIN** returns all records from the left table and the matching records from the right table. If there is no match, it returns `NULL` for columns from the right table.

### Syntax:
```sql
SELECT table1.column, table2.column
FROM table1
LEFT JOIN table2
ON table1.col = table2.col;
```

### Example:
```sql
SELECT employees.name, departments.department_name
FROM employees
LEFT JOIN departments
ON employees.department_id = departments.id;
```
This query returns all employees, even if they are not assigned to a department (with `NULL` for `department_name` if missing).

---

## 3. RIGHT JOIN  
A **RIGHT JOIN** returns all records from the right table and the matching records from the left table. If there is no match, it returns `NULL` for columns from the left table.

### Syntax:
```sql
SELECT table1.column, table2.column
FROM table1
RIGHT JOIN table2
ON table1.col = table2.col;
```

### Example:
```sql
SELECT employees.name, departments.department_name
FROM employees
RIGHT JOIN departments
ON employees.department_id = departments.id;
```
This query ensures all departments are listed, even if they have no employees (employees column will be `NULL` if no match).

---

## 4. FULL OUTER JOIN (Not Supported in MySQL)  
MySQL does **not** support `FULL OUTER JOIN` directly. However, you can achieve the same effect using a **UNION** of `LEFT JOIN` and `RIGHT JOIN`.

### Workaround:
```sql
SELECT employees.name, departments.department_name
FROM employees
LEFT JOIN departments
ON employees.department_id = departments.id
UNION
SELECT employees.name, departments.department_name
FROM employees
RIGHT JOIN departments
ON employees.department_id = departments.id;
```
This will return all employees and all departments, ensuring no data is lost.

---

### Summary:
| Join Type   | Returns |
|-------------|---------|
| **INNER JOIN** | Only matching rows from both tables |
| **LEFT JOIN**  | All rows from the left table + matching rows from the right table (NULL if no match) |
| **RIGHT JOIN** | All rows from the right table + matching rows from the left table (NULL if no match) |
| **FULL OUTER JOIN** (Not in MySQL) | All rows from both tables (use UNION workaround) |

---

✅ **Tip:** Always choose the right join type based on what data you need to include! 🚀

