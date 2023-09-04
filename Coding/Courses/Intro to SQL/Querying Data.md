## count
counts the number of records with a value in a field. 
```sql
SELECT COUNT(birthdate) FROM employees;

-- this gives us the number of non null values in each field
SELECT COUNT(birthdate), COUNT(name) FROM employees;

-- this gives us the number of rows in the table
SELECT COUNT(*) FROM employees;

-- gives the number of distinct birthdates
SELECT COUNT(DISTINCT birthdate) FROM employees;
```

## filtering numbers
- `<` less than
- `>` greater than
- `=` equal to
- `<>` not equal to
```sql
SELECT name 
FROM films
WHERE release_year > 1990;
```

## filtering strings
- `=` equal to
- `<>` not equal
- `LIKE` matches pattern, paired with `%`(0 or more characters) and `_`(a single character)
- `NOT LIKE` does not match pattern
- `ILIKE` case insensitive
- `NOT ILIKE` case insensitive
```sql
SELECT name
FROM films
WHERE language = 'Spanish';
```
Note: strings _MUST_ be enclosed in single quotes `''`. 

## multiple criteria
_OR_, _AND_, _BETWEEN_, _IN_, _NOT IN_

```sql
-- the following are equivalent
SELECT name
FROM films
WHERE release_year = 1990 OR release_year = 2000;

SELECT name
FROM films
WHERE release_year in (1990, 2000);
```
Note we need to repeat the field `release_year`

```sql
-- the following are equivalent
SELECT title
FROM films
WHERE release_year BETWEEN 1994 AND 2000;

SELECT title
FROM films
WHERE release_year >=1994 AND release_year <=2000;
```

## null
represents _missing value_
`IS NULL`, `IS NOT NULL` 
```sql
SELECT * 
FROM table_name 
WHERE column_name IS NULL;
```