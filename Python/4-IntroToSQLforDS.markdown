## Introduction to SQL for Data Science 
##### Basic manipulate functions for SQL
* select & distinct
* filtering results
* WHERE Clause, AND, OR, BETWEEN...AND..., LIKE and NOT LIKE (x%,_x%)
##### Aggregate functions
* AVG,SUM,MAX,MIN
  * example: 
    ```sql
    select AVG(budget) from films;
    select MAX(budget) from films;
    select MIN(budget) from films;
    select SUM(budget) from films;
    ```
* AS aliasing
##### Sorting, grouping,and joins
* ORDER BY w/ and w/o DESC - default order alphabetically. 
* GROUP BY: always goes after FROM clause. note: order by always goes after group by. 
* HAVING 
  note: aggregate functions can't be used in WHERE clause
* LIMIT 
* JOIN

## Joining Data in SQL
