# Triggers and Events in MySQL

## 🔹 Triggers in MySQL

### What is a Trigger?
A **Trigger** is an automatic action executed in response to certain events on a specified table. It helps maintain data integrity and automates certain database operations.

### 🔹 Types of Triggers
- **BEFORE Trigger**: Executes before the triggering event.
- **AFTER Trigger**: Executes after the triggering event.

### 🔹 Syntax for Creating a Trigger
```sql
CREATE TRIGGER trigger_name
BEFORE | AFTER INSERT | UPDATE | DELETE
ON table_name
FOR EACH ROW
BEGIN
    -- SQL statements here
END;
```

### 🔹 Example: BEFORE INSERT Trigger
```sql
CREATE TRIGGER BeforeInsertEmployee
BEFORE INSERT ON employees
FOR EACH ROW
BEGIN
    SET NEW.created_at = NOW();
END;
```
🔹 **Explanation**: Automatically sets `created_at` timestamp when a new row is inserted into the `employees` table.

### 🔹 Example: AFTER UPDATE Trigger
```sql
CREATE TRIGGER AfterUpdateSalary
AFTER UPDATE ON employees
FOR EACH ROW
BEGIN
    INSERT INTO salary_log (emp_id, old_salary, new_salary, change_date)
    VALUES (OLD.id, OLD.salary, NEW.salary, NOW());
END;
```
🔹 **Explanation**: Records every salary change in the `salary_log` table after an update.

### 🔹 Deleting a Trigger
```sql
DROP TRIGGER IF EXISTS trigger_name;
```

---

## 🔹 Events in MySQL

### What is an Event?
A **Scheduled Event** in MySQL allows executing SQL statements at specific time intervals. It automates repetitive tasks like backups and data cleanup.

### 🔹 Enabling Event Scheduler
```sql
SET GLOBAL event_scheduler = ON;
```

### 🔹 Creating an Event
```sql
CREATE EVENT event_name
ON SCHEDULE EVERY 1 DAY
DO
BEGIN
    -- SQL statements here
END;
```

### 🔹 Example: Auto Cleanup Log Table
```sql
CREATE EVENT CleanupOldLogs
ON SCHEDULE EVERY 7 DAY
DO
BEGIN
    DELETE FROM logs WHERE log_date < NOW() - INTERVAL 30 DAY;
END;
```
🔹 **Explanation**: Deletes logs older than 30 days every 7 days.

### 🔹 Viewing Scheduled Events
```sql
SHOW EVENTS;
```

### 🔹 Dropping an Event
```sql
DROP EVENT IF EXISTS event_name;
```

## 🔹 When to Use Triggers and Events?
- Use **Triggers** for **data validation, logging, or automation** on row-level changes.
- Use **Events** for **automated tasks like scheduled backups, cleanups, or periodic updates**.

---
✅ **Triggers and Events help automate and maintain MySQL databases efficiently!** 🚀

