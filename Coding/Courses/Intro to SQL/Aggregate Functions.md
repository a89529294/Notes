Return a single value. The following are some common _aggregate functions_.
- AVG() - only for numeric data types
- SUM() - only for numeric data types
- MIN() 
- MAX()
- COUNT()
- ROUND(number_to_round, decimal_places)

```sql
SELECT MIN(duration) AS shortest_film
FROM films;
```

If an _aggregate function_ is used in `SELECT` without `GROUP BY` in a query, then it applies to the whole table, However, if there is a `GROUP BY` then it applies on each group.

Note that you cannot use _aggregate functions_ in `WHERE` clauses since `WHERE` filters individual records; `HAVING` filters grouped records. From [[Execution Order]] you can see why as well. Only after `GROUP BY` we are allowed to use _aggregate functions_.