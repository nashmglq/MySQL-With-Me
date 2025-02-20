# MySQL String Functions

MySQL provides various string functions to manipulate and process string data. Below are some commonly used string functions:

## 🔹 String Manipulation Functions

### `CONCAT()`
Combines two or more strings into one.
```sql
SELECT CONCAT('Hello', ' ', 'World');  -- Output: Hello World
```

### `CONCAT_WS()`
Concatenates strings with a separator.
```sql
SELECT CONCAT_WS('-', '2025', '02', '20');  -- Output: 2025-02-20
```

### `LENGTH()`
Returns the length of a string in bytes.
```sql
SELECT LENGTH('Hello');  -- Output: 5
```

### `CHAR_LENGTH()`
Returns the number of characters in a string.
```sql
SELECT CHAR_LENGTH('Hello');  -- Output: 5
```

### `UPPER()` / `LOWER()`
Converts a string to uppercase or lowercase.
```sql
SELECT UPPER('hello');  -- Output: HELLO
SELECT LOWER('WORLD');  -- Output: world
```

### `LEFT()` / `RIGHT()`
Extracts a specified number of characters from the left or right side of a string.
```sql
SELECT LEFT('Hello', 2);  -- Output: He
SELECT RIGHT('World', 3);  -- Output: rld
```

### `SUBSTRING()` / `MID()`
Extracts a substring from a string.
```sql
SELECT SUBSTRING('Database', 3, 4);  -- Output: taba
SELECT MID('Database', 3, 4);  -- Output: taba
```

### `REPLACE()`
Replaces occurrences of a substring within a string.
```sql
SELECT REPLACE('Hello World', 'World', 'MySQL');  -- Output: Hello MySQL
```

### `REVERSE()`
Reverses a string.
```sql
SELECT REVERSE('MySQL');  -- Output: LQSyM
```

## 🔹 Trimming Functions

### `TRIM()`
Removes leading and trailing spaces.
```sql
SELECT TRIM('   Hello World   ');  -- Output: Hello World
```

### `LTRIM()` / `RTRIM()`
Removes leading or trailing spaces from a string.
```sql
SELECT LTRIM('   Hello');  -- Output: Hello
SELECT RTRIM('World   ');  -- Output: World
```

## 🔹 Pattern Matching Functions

### `LIKE`
Performs pattern matching using `%` (wildcard for multiple characters) and `_` (wildcard for a single character).
```sql
SELECT * FROM users WHERE name LIKE 'J%';  -- Names starting with 'J'
SELECT * FROM users WHERE name LIKE '_a%';  -- Names where the second letter is 'a'
```

### `LOCATE()` / `INSTR()`
Finds the position of a substring within a string.
```sql
SELECT LOCATE('SQL', 'MySQL');  -- Output: 3
SELECT INSTR('MySQL', 'SQL');  -- Output: 3
```

## 🔹 Encoding and Decoding Functions

### `ASCII()`
Returns the ASCII value of the first character in a string.
```sql
SELECT ASCII('A');  -- Output: 65
```

### `CHAR()`
Returns the character for a given ASCII value.
```sql
SELECT CHAR(65);  -- Output: A
```

## 🔹 String Formatting Functions

### `FORMAT()`
Formats a number as a string with a specified number of decimal places.
```sql
SELECT FORMAT(1234.5678, 2);  -- Output: 1,234.57
```

### `LPAD()` / `RPAD()`
Pads a string to a certain length with a specified character.
```sql
SELECT LPAD('MySQL', 10, '*');  -- Output: *****MySQL
SELECT RPAD('MySQL', 10, '-');  -- Output: MySQL-----
```

These functions are useful for string manipulation, searching, formatting, and trimming in MySQL databases. 🚀

