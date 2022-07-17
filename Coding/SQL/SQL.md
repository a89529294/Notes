- **SQL (Structured Query Language)** is a domain-specific language designed to handle data in tables.
- **DSL (Domain Spedific Language)** is a programming language with a higher level of abstraction optimized for a specific class of problems.
- The following are some **common SQL statements**: (MYSQL)

```plsql
CREATE DATABASE students;
```

```plsql
CREATE TABLE students_info (
			student_id INT,
			name VARCHAR(30),
			surname VARCHAR(30),
			age INT
);
```

```plsql
DROP DATABASE students;
```

```plsql
DROP TABLE students_info;
```

- **Basic Structures of a SELECT Statement**: 
	- `SELECT val1 [AS name1], ..., valN [AS nameN];`
	- ```plsql
	SELECT  
    col1 [AS alias1], ..., colN [AS aliasN]    
FROM  
    table_name  
;