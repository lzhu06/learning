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
1. Keys and superkeys - keep uniqueness 
1. Primary Keys - referal to other table & unique
   ```sql
   -- Specifying primary keys
   CREATE TABLE products (
       product_no integer UNIQUE NOT NULL,
       name text,
       price numeric
   );
   CREATE TABLE products (
       product_no integer PRIMARY KEY,
       name text,
       price numeric
   );
   CREATE TABLE products (
      a integer,
      b integer,
      c integer,
      PRIMARY KEY (a,c) -- combinationa of two coloumns as primary key
   );
   -- Add primary key constraints 
   ALTER TABLE table_name
   ADD CONSTRAINT some_name PRIMARY KEY (column_name)
   ```
1. Surrogate Keys
   ```sql
   ALTER TABLE table_name
   ADD COLUMN column_c varchar(256);
   
   UPDATE table_name
   SET column_c = CONCAT(column_a, column_b); - contact groups 
   
   ALTER TABLE table_name
   ADD CONSTRAINT pk PRIMARY KEY (column_c)；
   ```
##### Model1: N relationships with foreign keys
```sql
-- Select all professors working for universities in the city of Zurich
SELECT professors.lastname, universities.id, universities.university_city
from professors
join universities
ON professors.university_id = universities.id
where universities.university_city = 'Zurich';
```
###### More complex relationships 
###### Referential integrity 
1. DELETE NO ACTION - trigger errors if delete value in b but referenced by a. Throw an error.
1. DELECT CASCADE - trigger deletion in both table b and a. Delete all referencing records.
1. RESTRICT: Throw an error
1. SET NULL: set the referencing column to null
1. SET DEFAULT: Set the referencing column to its default value
###### Roundup
