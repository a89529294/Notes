For all _set operations_ the number of selected columns and their respective data types must be _identical_.
The resulting set's column names come from the first table, whether aliased or not.

## union & union all
They simply add up all the rows in each table, _UNION_ drops any duplicates but _UNION ALL_ keeps all.
```plsql
SELECT * 
FROM left_table
UNION
SELECT *
FROM right_table

SELECT * 
FROM left_table
UNION ALL
SELECT *
FROM right_table
```

## intersect
It effectively returns the intersection of the two result sets, keeping only the rows that are present in both tables based on their selected column values.

```plsql
SELECT student_name 
FROM students 
INTERSECT 
SELECT student_name 
FROM enrolled_students;
```

## except
The `EXCEPT` operator is used to retrieve the rows from the first query result set that are not present in the second query result set.

```plsql
SELECT student_name 
FROM students 
EXCEPT 
SELECT student_name 
FROM enrolled_students;
```