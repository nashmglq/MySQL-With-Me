# MySQL Window Functions

## Overview
Window functions perform calculations across a set of table rows related to the current row. Unlike aggregate functions, they do not collapse rows but retain them while computing values.

## Syntax
```sql
SELECT column_name,
       window_function() OVER (
           PARTITION BY column_name
           ORDER BY column_name
       ) AS alias_name
FROM table_name;
```

## Common Window Functions

### 🔹 ROW_NUMBER()
Assigns a unique sequential integer to rows within a partition.
```sql
SELECT id, name,
       ROW_NUMBER() OVER (PARTITION BY department ORDER BY salary DESC) AS row_num
FROM employees;
```

### 🔹 RANK()
Assigns a rank to each row within a partition. Equal values receive the same rank, and the next rank is skipped.
```sql
SELECT id, name,
       RANK() OVER (PARTITION BY department ORDER BY salary DESC) AS rank_num
FROM employees;
```

### 🔹 DENSE_RANK()
Similar to RANK(), but without gaps in ranking.
```sql
SELECT id, name,
       DENSE_RANK() OVER (PARTITION BY department ORDER BY salary DESC) AS dense_rank
FROM employees;
```

### 🔹 NTILE(n)
Divides rows into `n` number of roughly equal parts.
```sql
SELECT id, name,
       NTILE(4) OVER (ORDER BY salary DESC) AS quartile
FROM employees;
```

### 🔹 LAG()
Retrieves the value from the previous row within a partition.
```sql
SELECT id, name, salary,
       LAG(salary) OVER (PARTITION BY department ORDER BY salary) AS prev_salary
FROM employees;
```

### 🔹 LEAD()
Retrieves the value from the next row within a partition.
```sql
SELECT id, name, salary,
       LEAD(salary) OVER (PARTITION BY department ORDER BY salary) AS next_salary
FROM employees;
```

### 🔹 FIRST_VALUE()
Returns the first value in a window frame.
```sql
SELECT id, name, salary,
       FIRST_VALUE(salary) OVER (PARTITION BY department ORDER BY salary) AS min_salary
FROM employees;
```

### 🔹 LAST_VALUE()
Returns the last value in a window frame.
```sql
SELECT id, name, salary,
       LAST_VALUE(salary) OVER (PARTITION BY department ORDER BY salary RANGE BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) AS max_salary
FROM employees;
```

## Conclusion
Window functions provide powerful analytical capabilities in MySQL, allowing for calculations across partitions of data without losing row-level details. 🚀

