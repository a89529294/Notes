## DISTINCT keyword
`SELECT DISTINCT name FROM employees;`
`SELECT DISTINCT name, dep_id FROM employees;` this means the combination of `name` and `dep_id` is unique.

## aliasing
`SELECT name AS first_name FROM employees;`

## views
A virtual table that is the saved result of a SQL `SELECT` statement.
When accessed, views automatically update in response to updates in the underlying data.
Think of it as _saved select statement_. 

```sql
-- Your code to create the view:
CREATE VIEW library_authors AS
SELECT DISTINCT author AS unique_author
FROM books;

-- Select all columns from library_authors
SELECT * FROM library_authors;
```

## bad field or table names
For identifiers with sensitive characters such as _space_, _dash_ etc you need to enclose it with _double quotes_.
```sql
SELECT "first name"
FROM people;
```