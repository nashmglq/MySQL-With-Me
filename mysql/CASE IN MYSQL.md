# MySQL Case Statements

## 🔹 What is a CASE Statement?

A `CASE` statement in MySQL allows conditional logic within SQL queries, similar to `IF-ELSE` statements in programming languages. It is useful for applying conditional expressions in `SELECT`, `UPDATE`, `INSERT`, and `ORDER BY` clauses.

---

## 🔹 Simple CASE Statement

Matches an expression against a set of values and returns the corresponding result.

```sql
SELECT column_name,
    CASE column_name
        WHEN 'Value1' THEN 'Result1'
        WHEN 'Value2' THEN 'Result2'
        ELSE 'DefaultResult'
    END AS alias_name
FROM table_name;
```

✅ **Example:** Categorizing users based on age

```sql
SELECT name, age,
    CASE age
        WHEN 18 THEN 'Teen'
        WHEN 25 THEN 'Young Adult'
        ELSE 'Other'
    END AS age_category
FROM users;
```

---

## 🔹 Searched CASE Statement

Evaluates conditions separately and returns a result based on the first matching condition.

```sql
SELECT column_name,
    CASE
        WHEN condition1 THEN 'Result1'
        WHEN condition2 THEN 'Result2'
        ELSE 'DefaultResult'
    END AS alias_name
FROM table_name;
```

✅ **Example:** Categorizing salary levels

```sql
SELECT employee_name, salary,
    CASE
        WHEN salary >= 80000 THEN 'High Salary'
        WHEN salary >= 50000 THEN 'Medium Salary'
        ELSE 'Low Salary'
    END AS salary_category
FROM employees;
```

---

## 🔹 CASE in ORDER BY

Used to customize sorting based on conditions.

✅ **Example:** Sorting users by age category

```sql
SELECT name, age
FROM users
ORDER BY
    CASE
        WHEN age < 18 THEN 1
        WHEN age BETWEEN 18 AND 25 THEN 2
        ELSE 3
    END;
```

---

## 🔹 CASE in UPDATE

Used to update records conditionally.

✅ **Example:** Updating order status

```sql
UPDATE orders
SET status =
    CASE
        WHEN shipped = 1 THEN 'Shipped'
        WHEN canceled = 1 THEN 'Canceled'
        ELSE 'Processing'
    END;
```

---

## 🔹 CASE in GROUP BY

Used to group data conditionally.

✅ **Example:** Counting users by age group

```sql
SELECT
    CASE
        WHEN age < 18 THEN 'Minor'
        WHEN age BETWEEN 18 AND 25 THEN 'Young Adult'
        ELSE 'Adult'
    END AS age_group,
    COUNT(*) AS user_count
FROM users
GROUP BY age_group;
```

---

## 🔹 Summary

✅ **Key Points:**
- `CASE` works like `IF-ELSE` logic in SQL.
- Supports `WHEN-THEN` conditions.
- Can be used in `SELECT`, `ORDER BY`, `UPDATE`, and `GROUP BY`.
- Ensures flexibility in SQL queries.

📌 Use `CASE` whenever dynamic logic is needed within SQL queries! 🚀

