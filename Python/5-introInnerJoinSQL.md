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
