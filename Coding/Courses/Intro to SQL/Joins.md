The following example include tables with the following schema
```
states table 
country VARCHAR
indep_year YEAR

presidents table
country VARCHAR
continent VARCHAR
president VARCHAR

prime_ministers table
country VARCHAR
continent VARCHAR
prime_minister VARCHAR

monarchs table 
country VARCHAR
continent VARCHAR
monarch VARCHAR

prime_minister_terms table
prime_minister VARCHAR
pm_start YEAR
```

## inner join
`inner join` looks for records in both tables that match on a given field. The field can be different on each table. 

```plsql
SELECT prime_ministers.country, prime_ministers.continent, prime_minister, president
FROM prime_ministers
INNER JOIN presidents
on prime_ministers.country = presidents.country;

-- to simplify we can use aliases for our tables
SELECT p1.country, p1.continent, prime_minister, president
FROM prime_ministers AS p1
INNER JOIN presidents AS p2
on p1.country = p2.country;

-- to simplify further we can use USING if matching on identical field names
SELECT p1.country, p1.continent, prime_minister, president
FROM prime_ministers AS p1
INNER JOIN presidents AS p2
USING(country);
```
- if a column exist in both tables we need to prefix it with the table name. Unless the column is used in the `ON` or `USING` condition.
- `USING(common_col1, common_col2,...)` allows for more than one column. This allows two tables to match on multiple columns with the same names.
- `ON` allows us to join on multiple columns as well, `ON p1.country = p2.country AND p1.continent = p2.continent`.

## outer joins
_left join_, _right join_, _full outer join_

### left join
Returns all records in the left table, and records in the right table that match on the joining field. Every row in A will show up 1 to many times.

```plsql
SELECT *
FROM left_table
LEFT JOIN right_table
ON left_table.id = right_table.id
```

### right join
Returns all records in the right table, and records in the left table that match on the joining field.

```plsql
SELECT *
FROM left_table
RIGHT JOIN right_table
ON left_table.id = right_table.id
```

### full join
Combines the results of _left join_ and _right join_.

## cross join
Combines all rows from two or more tables without any specific join condition. It creates every possible combination of rows from the involved tables. 
Note there is no `ON` clause.
Note you can create an _implicit cross join_ by `FROM table1, table2`

```plsql
SELECT *
FROM table_1
CROSS JOIN table_2;
```



## self join
_Self join_ is not a like the previous joins in the sense it doesn't come with a special keyword.
It simply means joining table with itself, you can use any previous joins to do so. 
Note you need to alias table names in this case.
```plsql

```