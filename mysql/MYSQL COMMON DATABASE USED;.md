# MySQL Notes

## How to Create a Database?
```sql
CREATE DATABASE database_name;
```

## How to Create a Table for That Database?
```sql
CREATE TABLE table_name (
    column1 INT NOT NULL,  -- For integers
    column2 VARCHAR(255) NOT NULL,  -- For characters
    column3 INT PRIMARY KEY AUTO_INCREMENT,  -- Primary key with auto-increment
    
    FOREIGN KEY (column_current_table) REFERENCES referenced_table(column_referenced_table)
);
```

## How to Alter Table Data Type?
```sql
ALTER TABLE table_name
MODIFY COLUMN column_name datatype;
```

## How to Add a New Column in a Table?
```sql
ALTER TABLE table_name
ADD column_name datatype;
```

## How to Drop a Column from a Table?
```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

## How to Alter the Name of a Column?
```sql
ALTER TABLE table_name
RENAME COLUMN old_name TO new_name;
```

## How to Drop a Table?
```sql
DROP TABLE table_name;
```

## Joins in MySQL

### Inner Joins
```sql
SELECT table1.column, table2.column 
FROM table1 
INNER JOIN table2
ON table1.col = table2.col;
```

## MySQL Queries

### Check Current Database
```sql
SELECT DATABASE();
```

### Modify Column Values Temporarily
```sql
SELECT age + 10 FROM books; -- Adds 10 to the age column
```

### Commenting in MySQL
```sql
# This is a comment
```

### MySQL Follows PEMDAS
**PEMDAS = Parentheses, Exponents, Multiply/Divide, Addition/Subtraction**

## DISTINCT in MySQL
```sql
SELECT DISTINCT column_name FROM table_name; -- Removes duplicate values
```

## WHERE Clause
Allows conditions using `<, >, !=, OR, AND`.

## LIKE Statement
Searches for patterns using `%` (wildcards) and `_` (specific character placeholders).
```sql
SELECT * FROM table_name WHERE column_name LIKE '%pattern%';
```

### Examples:
- `%of%` → Finds any value containing "of"
- `of%` → Finds values starting with "of"
- `%of` → Finds values ending with "of"
- `World __ World` → Finds "World (two characters) World"

## ORDER BY Clause
```sql
SELECT column_name FROM table_name ORDER BY column_name ASC; -- Ascending order
SELECT column_name FROM table_name ORDER BY column_name DESC; -- Descending order
```

## Aggregate Functions
```sql
COUNT(), SUM(), AVG(), MAX(), MIN()
```

## GROUP BY Clause
Groups rows with the same values.
```sql
SELECT column_name, AVG(column_name) FROM table_name GROUP BY column_name;
```

**Rule:** Cannot use two columns in GROUP BY without aggregation unless both are in GROUP BY.

## AS (Alias)
```sql
SELECT column_name, AVG(column_name) AS temp_name FROM table_name GROUP BY column_name;
```

## HAVING vs WHERE
```sql
-- Invalid because AVG() is calculated after GROUP BY
SELECT department, AVG(age) FROM employee WHERE AVG(age) > 35 GROUP BY department;

-- Correct usage
SELECT department, AVG(age) FROM employee GROUP BY department HAVING AVG(age) > 35;
```

### Combination of HAVING and GROUPING
```sql
SELECT department, age, AVG(salary)  
FROM employee  
WHERE age > 30  
GROUP BY department, age  
HAVING AVG(salary) > 5000;
```

## LIMIT Clause
Restricts the number of rows returned.
```sql
SELECT * FROM employee LIMIT 3; -- Returns 3 rows
SELECT * FROM employee LIMIT 3,1; -- Skips 3 rows, returns 1
```

## Common MySQL Data Types

### Numeric Types:
- `INT`: `INT(11)` (e.g., 12345)
- `FLOAT`: `FLOAT(7,4)` (e.g., 3.1415)
- `DOUBLE`: `DOUBLE(16,8)` (e.g., 123.45678901)
- `DECIMAL`: `DECIMAL(10,2)` (e.g., 150.75)
- `TINYINT`: `TINYINT(1)` (e.g., 0 or 1)
- `SMALLINT`: `SMALLINT(5)` (e.g., 3000)

### String Types:
- `VARCHAR`: `VARCHAR(255)` (e.g., 'John Doe')
- `CHAR`: `CHAR(10)` (e.g., 'A123456789')
- `TEXT`: `TEXT` (e.g., 'This is a long text field.')
- `BLOB`: `BLOB` (binary data, e.g., for images)

### Date/Time Types:
- `DATE`: `DATE` (e.g., '2025-02-06')
- `DATETIME`: `DATETIME` (e.g., '2025-02-06 12:30:00')
- `TIMESTAMP`: `TIMESTAMP` (e.g., '2025-02-06 12:30:00')
- `TIME`: `TIME` (e.g., '12:30:00')
- `YEAR`: `YEAR` (e.g., '2025')

### Other Types:
- `ENUM`: `ENUM('small', 'medium', 'large')` (e.g., 'medium')
- `SET`: `SET('A', 'B', 'C')` (e.g., 'A,B')
- `BOOLEAN`: `BOOLEAN` (e.g., TRUE or FALSE)

