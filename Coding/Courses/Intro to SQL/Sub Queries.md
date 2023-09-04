`WHERE` is the most common place for subqueries. The second most common place is inside `SELECT`. The third is in `FROM`.

```plsql
SELECT *
FROM some_table
WHERE some_field IN (4, 8, 12);

-- subquery in WHERE
SELECT *
FROM some_table
WHERE some_field IN (subquery here);

-- subquery in SELECT
SELECT DISTINCT continent, (SELECT COUNT(*) FROM monarchs WHERE states.continent = monarchs.continent) AS monarch_count 
FROM states;

-- subquery in FROM
SELECT DISTINCT monarchs.continent, sub.most_recent
FROM monarchs, 
	(SELECT continent, MAX(indep_year) AS most_recent 
	FROM states
	GROUP BY continent) AS sub -- temp table name
WHERE monarchs.continent = sub.continent

-- remember FROM table1, table2 creates an implicit CROSS JOIN
```

The _subquery in SELECT_ is tricky, here is how to interpret it
1. The `SELECT DISTINCT continent` part of the query retrieves a list of unique continent names from the "states" table. This creates a result set with one row for each unique continent found in the "states" table.
2. The subquery `(SELECT COUNT(*) FROM monarchs WHERE states.continent = monarchs.continent) AS monarch_count` is executed for each row produced by the first part of the query. In other words, it runs separately for each distinct continent name retrieved in the first part.
3. Inside the subquery, `states.continent` refers to the continent name from the current row being processed in the outer query. The subquery counts how many rows in the "monarchs" table have a matching continent name.
4. The subquery's result is given an alias, "monarch_count," and this value is associated with the corresponding continent name from the outer query's result.