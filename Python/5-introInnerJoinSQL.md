### Introduction to Inner Join - SQL
#### Inner Join / outter join / different type of join - intersection part 
1. left_table & right_table
1. syntax of inner join:
    ```SQL
    select p1.col_name1,p1.col_name2,col_name3,col_name4
    from table1 as p1
    inner join table2 as p2
    on p1.col_name1 = p2.col_name2
    --add more inner join
    inner join table3 as p3
    on p1.col_name1 = p3.col_name3 and p2.col_name2 = p3.col_name3
    ```
 1. Inner Join via USING: if col_name is the same in both left and right table. 
     ```SQL
    select p1.col_name1,p1.col_name2,col_name3,col_name4
    from table1 as p1
    inner join table2 as p2
    using (id) -- if id is the same in both two tables
     ```
 1. Self-ish joins,just in "CASE"
    ```SQL
    select x1,x2,x3,
    case when ____ <_____ then 'some defined tags'
         when ____ < = _____ then ' some defined tags'
         else '_____' end
         as defined_colname
    from table_name
    order by defined_colname;
    ```
#### Outter Joins: reaching out to other tables - 3 types of outter joins: LEFT/RIGHT/FULL JOINs
1. LEFT JOIN: keep all columns and values in the left table and matching the value in the right table. For non-matching value, will show missing / empty value. syntax as follow:
    ```SQL
    SELECT P1.COUNTRY, COL_NAME1,COL_NAME2
    FROM TABLE1 AS P1
    LEFT JOIN TABLE2 AS P2
    ON P1.COUNTRY = P2.COUNTRY;
    ```
 1. RIGHT JOIN: keep all columns and values in the right table and matching the value in the left table. For non-matching value, will show missing / empty vlue. Syntax as follow:
    ```SQL
    SELECT P1.COUNTRY, COL_NAME, COL_NAME2
    FROM TABLE1 AS P1
    RIGHT JOIN TABLE2 AS P2
    ON P1.COUNTRY = P2.COUNTRY;
    ```
 1. FULL JOIN: keeps all values 
    ```SQL
    SELECT P1.COUNTRY,COL_NAME,COL_NAME2
    FROM TABLE1 AS P1
    FULL JOIN TABLE2 AS P2
    ON P1.COUNTRY = P2.COUNTRY;
    ```
1. CROSSing the Rubicon: cross join creates all possible combinations of tables.
   ```SQL
   select col_name1, col_name2
   from table1 as p1
   cross join table2 as p2
   where p1.col_name in ('','');
   ```
#### State of the UNION - venn diagrams
1. UNION: doesn't duplicate common values, only count once. UNION ALL: duplicate common values.
   ```sql
   select col_name as c1, col_name2
   from table1
   union --union or union all
   select col_name3,col_name4
   from table2
   order by col_name4
   ```
1. INTERSECT: common area 
   ```sql
   select id
   from left_table
   intersect
   select id
   from right_table;
   ```
1. EXCEPT: except area
   ```sql
   select id
   from left_table
   except
   select id
   from right_table;
   ```
1. Semi-joins (subqueries):matches key field in right table and picks the value in left table matches the key field in right table.
   ```sql
   SELECT president, country, continent
   FROM president
   WHERE country IN
    (SELECT name
        FROM states
        WHERE indep_year < 1800);
   ```
1. Anti-joins:picks the colums / rows in left table do not matches in right_table
   ```sql
   select president, country, continent
   from presidents
   where continent like '%America'
      and country not in
          (select name
           from states
           where indep_year < 1800);
   ```
#### Subqueries inside WHERE and SELECT clauses 
1. subquery inside where caluse set-up
   ```sql
   --Asian countries below average 'fert_rate'
   select name, fert_name
   from states
   where continent = 'Asia'
    and fert_rate < 
        (select avg(fert_rate)
         from states);
   ```
 1. Subqueries inside SELECT clauses 
    ```sql
    select distinct continent,
      (select count(*)
       from states
       where prime_ministers.continent = states.continent) as countries_sum
    from prime_ministers;
    ```
 1. Subqueries inside FROM clauses
    ```sql
    select distinct monarchs.continent,subquery.max_perc
    from monarchs,
      (select continent, MAX(women_parli_perc) as max_perc
       from states
       group by continent) as subquery
    where monarchs.continent = subquery.continent
    order by continent;
    ```
