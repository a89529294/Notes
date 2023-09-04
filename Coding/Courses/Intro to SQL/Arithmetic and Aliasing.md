```sql
SELECT 4 + 3;
SELECT 4 * 3;
SELECT 4 / 3; -- 1
SELECT 4.0 / 1; -- 1.3333...
```

## arithmetic vs aggregate function
_aggregate functions_ work vertically, _arithmetic_ work horizontally.
```sql
SELECT SUM(gross) 
FROM films;

SELECT gross-budget
FROM films;
```