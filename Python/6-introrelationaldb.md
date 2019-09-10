### Introduction to relational databases 
##### Your first database 
1. real-life entities become tables
1. reduced redundancy
1. data integrity by relationships
##### By learning this course, you will know 3 concepts:
  * constraints
  * keys
  * referntial integrity
##### Create table and identify entity data type
```sql
--Create tables
CREATE table_name (
col_name1 char
col_name2 num
col_name3 char(5)
);
--Add column
ALTER TABLE table_name
ADD col_name_new datatype;
```
##### Update your database as structure changes
1. Insert distinct records into the new tables
   ```sql
   --Insert Into statement
   INSERT INTO table_name (col_a, col_b)
   VALUES ("value_a","value_b")
   -- Insert Into Example
   INSERT INTO organizations
   SELECT DISTINCT organization,
      organization_sector
   FROM university_professors;
   ```
1. Rename a column in affiliations table
   ```sql
   CREATE TABLE affiliations (
     firstname text
     lastname text
     university_shortname text,
     function text,
     organisation text
   );
   --rename statement
   ALTER TABLE table_name
   RENAME COLUMN old_name TO new_name
   ```
1. DROP COLUMN - Delete column 
   ```sql
   ALTER TABLE table_name
   DROP COLUMN column_name
   ```
##### Better data quality with constraints 
###### Integrity constraints
1. Attribute constraints 
1. Key constraints
1. Referential integrity constraints 
###### Dealing with data types (casting)
1. CAST (COL_NAME AS data_type)
###### Working with data types
