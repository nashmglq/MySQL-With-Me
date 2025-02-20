# Stored Procedures in MySQL

## 🔹 What is a Stored Procedure?
A **Stored Procedure** is a set of SQL statements that are stored in the database and can be executed repeatedly. It helps in **code reusability**, **performance optimization**, and **security**.

## 🔹 Benefits of Stored Procedures
- **Encapsulation**: Groups multiple SQL statements into a single block.
- **Performance Optimization**: Reduces network traffic and improves execution speed.
- **Reusability**: Can be called multiple times to avoid redundant code.
- **Security**: Limits direct access to tables by allowing controlled data operations.

## 🔹 Creating a Stored Procedure
```sql
DELIMITER //
CREATE PROCEDURE procedure_name()
BEGIN
    -- SQL statements here
END //
DELIMITER ;
```

### Example:
```sql
DELIMITER //
CREATE PROCEDURE GetAllEmployees()
BEGIN
    SELECT * FROM employees;
END //
DELIMITER ;
```

## 🔹 Calling a Stored Procedure
```sql
CALL GetAllEmployees();
```

## 🔹 Stored Procedure with Parameters
### 🔹 IN Parameter (Input Only)
```sql
DELIMITER //
CREATE PROCEDURE GetEmployeeByID(IN emp_id INT)
BEGIN
    SELECT * FROM employees WHERE id = emp_id;
END //
DELIMITER ;
```
#### Call:
```sql
CALL GetEmployeeByID(101);
```

### 🔹 OUT Parameter (Output Only)
```sql
DELIMITER //
CREATE PROCEDURE GetEmployeeCount(OUT total_count INT)
BEGIN
    SELECT COUNT(*) INTO total_count FROM employees;
END //
DELIMITER ;
```
#### Call:
```sql
CALL GetEmployeeCount(@count);
SELECT @count;
```

### 🔹 INOUT Parameter (Both Input and Output)
```sql
DELIMITER //
CREATE PROCEDURE UpdateSalary(INOUT emp_salary DECIMAL(10,2))
BEGIN
    SET emp_salary = emp_salary * 1.10; -- Increases salary by 10%
END //
DELIMITER ;
```
#### Call:
```sql
SET @salary = 50000;
CALL UpdateSalary(@salary);
SELECT @salary; -- New updated salary
```

## 🔹 Modifying a Stored Procedure
```sql
DROP PROCEDURE IF EXISTS procedure_name;
```
Then, recreate it with modifications.

## 🔹 Deleting a Stored Procedure
```sql
DROP PROCEDURE procedure_name;
```

## 🔹 When to Use Stored Procedures?
- When you need **frequent SQL execution**.
- When you want to **secure table access**.
- When working with **complex business logic**.

---
✅ **Stored Procedures help streamline MySQL operations efficiently!** 🚀

