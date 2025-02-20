# MySQL Unions

## Unions in MySQL

Unions are used to combine the results of multiple SELECT queries into a single result set.

### 🔹 UNION

Combines the results of two SELECT queries and removes duplicate rows.

```sql
SELECT column1, column2 FROM table1
UNION
SELECT column1, column2 FROM table2;
```

### 🔹 UNION ALL

Combines the results of two SELECT queries without removing duplicate rows.

```sql
SELECT column1, column2 FROM table1
UNION ALL
SELECT column1, column2 FROM table2;
```

