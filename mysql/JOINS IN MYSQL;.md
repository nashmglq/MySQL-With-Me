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

