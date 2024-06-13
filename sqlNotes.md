# STUCTURED QUERY LANGUAGE

- SQL is a query language that communicates with databases.

- SQL can create , update, delete and retrieve data from databases like mySql , Oracle, PostgreSQL...

- Microsoft documention can be used to learn SQL.

## Database

- Database -> organized collection of structured data, usually controlled by DBMS.

### Features of Database
1. It is a special software, it stores data in hard disk but when data is frequently accessed it is stored in RAM.

2. Querying becomes easier

3. CRUD is easy

4. Backups are inbuilt

5. Undo - easily (time limit)

6. Performance


-  why can't we put a database in our laptop -> because many user requests can't be handled

- Database is stored in cloud

- Cloud is renting PC's

- Cloud Providers -> Azure , AWS , Google Cloud, IBM CLoud, Alibaba Cloud, Salesforce.

- AWS was the first to start cloud , that's why it is ahead of all

- Netflix was the first company to believe in AWS.

- Perks of renting instead of buying Databases

  1. High intial cost
  2. Rent room
  3. A/C
  4. Power Bill
  5. Maintenance (Swap harddisk when anything happens)
  6. Spares (Backup)
  7. Generator
  8. Disaster Management 
     - store DB in disaster prone areas
     - Backup Data 
  9. Scaling

- Linux operating system is used in cloud , as linux is the most used operating system .
  - Advantages of using linux 
      - Free
      - Open source 
      - Secure
      - Small footprint (take less space for installation, which means it costs less)
      - Automation (Managing everything from terminal)

- Linux has many flavours , they are called as distros

- Alpine distro of linux is used in cloud

![alt text](<Screenshot (28).png>)

## Scaling
 - Increasing number of customers
 - Vertical Scaling => to increase RAM or upgrading the processors (make it more powerful)
 - Horizontal Scaling => add more PC

 ![alt text](<Screenshot (29).png>)
 - Cloud has auto-scaling

 ![alt text](<Screenshot (30).png>)

 - DDOS Attack => increase fake traffic. Send fake traffic using bots. (Distributed Denial of Service)
 ![alt text](<Screenshot (31).png>)

 To prevent the attack, divert the traffic to a dummy website. To identify the traffic , block the IP addresses by identifying using region.
 Identifying the bot using captcha.


### SQL Vs NOSQL

- Sql data is stored in  tables.
   Eg:MySql(Microsoft) , PLSQL (Oracle) , PostgreSQL, Amazon RDS

- NoSql data is stored in documents
  Eg:MongoDB , DynamoDB , Firebase, Redis (good at faster retrieval of data->chaching), CouchDB, cassandra

- Query is a question 

- SELECT => to filter the columns

- WHERE => to filter the rows 

![alt text](<Screenshot (34)-1.png>)
![alt text](<Screenshot (36).png>)

- IN operator =>  its like OR operator
```sql
Select * From movies
Where year In(2001,2007,2010)
```

- to select distinct values
```sql
SELECT DISTINCT column, another_column, …
FROM mytable
WHERE condition(s);
```

- ORDER BY -> to sort query results
```sql
SELECT column, another_column, …
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC;
```

- LIMIT => whatever the result is it limits the number of rows to return .
OFFSET => to skip certain values.
- The LIMIT will reduce the number of rows to return, and the optional OFFSET will specify where to begin counting the number rows from.
```sql
SELECT column, another_column, …
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC
LIMIT num_limit OFFSET num_offset;
```



### NORMALIZATION

- to increase safety of data( avoid anamolies)

- When there is duplication of data it becomes difficult for updation and deletion and there will be a storage issue and causes inconsistency-> making separate tables makes it easy (Update anamoly).

- Data after separation into tables is called normalization.

- Primary Key 
  1. Unique
  2. Notnull
  3. One column per table

-  Two or more columns taken together can be considered as primary key -> composite primary key

- Foreign Key -> used to join tables (The primary key of one table will be foriegn key of another)

### 1NF
![alt text](<Screenshot (40).png>)

1) Using row order to convey information is not required
![alt text](<Screenshot (44).png>) ❌
![alt text](<Screenshot (43).png>)

2) Mixing Data types within the same column voilates 1NF
![alt text](<Screenshot (42).png>)

### 2NF

- To overcome updation , deletion and insertion anamoly
![alt text](<Screenshot (45).png>) 

- if the non-key attribute is not completely(entirely) dependent on the composite primary key then separate the column with the column of primary key on which it is dependent.

![alt text](<Screenshot (46).png>)

### 3NF

- There should be no dependency of non-key attribute on any other non-key attribute.
- In the below expample Player_rating is indirectly dependent on Player_ID and Player_Skill_Level is directly dependent on Player_ID.

![](<Screenshot (48).png>)
- Player_Skill_Level and Player_Rating are dependent on each other -> voilates 3NF
![alt text](<Screenshot (47).png>)

- bcnf => shorter version of 3NF => Every attribute in a table should depend on the key, the whole key. Primary key should also depend on primary key.


## JOINS
-  For safety we normalized the data, to get data from tables we use joins.

- We have two joins inner and outer

- outer join has left , right and full join

#### INNER JOIN

- Inner join => gives only common items of two tables

```sql
SELECT column, another_table_column, …
FROM mytable
INNER JOIN another_table 
    ON mytable.id = another_table.id
WHERE condition(s)
ORDER BY column, … ASC/DESC
LIMIT num_limit OFFSET num_offset;
```
- A join B on Pk = Fk;
![alt text](<Screenshot (50).png>)

![alt text](<Screenshot (49).png>)

#### Left Join
![alt text](<Screenshot (52).png>)
- We can convert left join to right join by exchanging the table names.

#### Right Join
![alt text](<Screenshot (51).png>)

#### FULL JOIN

![alt text](<Screenshot (53).png>)

## NULL AND NOT NULL

- you can test a column for NULL values in a WHERE clause by using either the IS NULL or IS NOT NULL constraint.
```sql
Select query with constraints on NULL values
SELECT column, another_column, …
FROM mytable
WHERE column IS/IS NOT NULL
AND/OR another_condition
AND/OR …;
```


### MATHEMATICAL OPERATIONS AND ALIAS
- we can do mathematical operations
```sql
SELECT particle_speed / 2.0 AS half_particle_speed
FROM physics_data
WHERE ABS(particle_position) * 10.0 > 500;
```
- If we have large column names we can use alias 
```sql
SELECT col_expression AS expr_description, …
FROM mytable;
```

### AGGREGATE FUNCTIONS
- Aggregation is summarization

```sql
SELECT AGG_FUNC(column_or_expression) AS aggregate_description, …
FROM mytable
WHERE constraint_expression;
```

![alt text](<Screenshot (58).png>)

- apply the aggregate functions to individual groups of data within that group.
This would then create as many results as there are unique groups defined as by the GROUP BY clause.

```sql
SELECT AGG_FUNC(column_or_expression) AS aggregate_description, …
FROM mytable
WHERE constraint_expression
GROUP BY column;
```
- The GROUP BY clause works by grouping rows that have the same value in the column specific

- When we want to drill down to next level we use grouping

- If there is every use group by .

### HAVING CLAUSE IN GROUP By
- HAVING clause which is used specifically with the GROUP BY clause to allow us to filter grouped rows from the result set.
```sql
Select query with HAVING constraint
SELECT group_by_column, AGG_FUNC(column_expression) AS aggregate_result_alias, …
FROM mytable
WHERE condition
GROUP BY column
HAVING group_condition;
```

- Both having and where are used for filtering .

## ORDER OF EXECUTION OF QUERIES
```sql
SELECT DISTINCT column, AGG_FUNC(column_or_expression), …
FROM mytable
    JOIN another_table
      ON mytable.column = another_table.column
    WHERE constraint_expression
    GROUP BY column
    HAVING constraint_expression
    ORDER BY column ASC/DESC
    LIMIT count OFFSET COUNT;
```

## INSERT STATEMENT

- inserting data into a database, we need to use an INSERT statement, 

- to insert values in all columns of table
```sql
INSERT INTO mytable
VALUES (value_or_expr, another_value_or_expr, …),
       (value_or_expr_2, another_value_or_expr_2, …),
       …;
```

- to insert into only specific columns
```sql
INSERT INTO mytable
(column, another_column, …)
VALUES (value_or_expr, another_value_or_expr, …),
      (value_or_expr_2, another_value_or_expr_2, …),
      …;
```


## UPDATE STATEMENT

-  update existing data, 
- Similar to the INSERT statement, you have to specify exactly which table, columns, and rows to update. In addition, the data you are updating has to match the data type of the columns in the table schema.

- First write select statement before update statement, so that we can confirm what we are updating first.
```sql
UPDATE mytable
SET column = value_or_expr, 
    other_column = another_value_or_expr, 
    …
WHERE condition;
```
eg:
```sql
Update Movies
Set Director = "John Lasseter"
Where Title="A Bug's Life";
```

## DELETE A ROW
```sql
DELETE FROM mytable
WHERE condition;
```
- If you decide to leave out the WHERE constraint, then all rows are removed

## Data Manipulation Language -> Select,Update,Delete,Insert
## Data Denifination Language -> Create,Alter,Drop 
## CREATE TABLE
- If there already exists a table with the same name, the SQL implementation will usually throw an error, so to suppress the error and skip creating a table if one exists, you can use the IF NOT EXISTS clause.
```sql
CREATE TABLE IF NOT EXISTS mytable (
    column DataType TableConstraint DEFAULT default_value,
    another_column DataType TableConstraint DEFAULT default_value,
    …
);
```
#### Data types
  1. Integer,Boolean
  2. FLoat, Double, Real 
     - float stores upto 3 precision points
     - double stores upto 6 precision points
     - real stores upto 12 prescision pints
  3. Character, varchar,text
     - CHARACTER are meant to store few characters (eg:gender)
     - VARCHAR are meant to store few sentences
     - TEXT for paragraphs
  4. date,datetime 
     -  Date stores date
     - Datetime stores date and time
  5. Blob -> to store binary data
     - to store Images , Videos 

- but using blob is not recommended , so image path is stored in database

##### Sql Server Data Types

1. Integer
   - Int (-2B,2B)
   - SmallInt (-32k,32k)
   - BigInt (-9 x 10^8 , 9 x 10^8)
2. String
   - varchar 
   - nvarchar - follows unicode (calculations are easier that is chinese character is stored as two characters in unicode). Supports diff languages
   ![alt text](<Screenshot (68).png>)
   - instead of text max is used
      - varchar(max)
      - nvarchar(max)
3. Decimal 
    - decimal -> exact stores 10,2 -> upto 2 decimals and 10 is the decimal system used.
    - float -> approx 
    - perfomance of float and approximation of decimal is good
4. boolean
    - bit -> stores either 0 or 1
5. Date and datetime


#### Table Constraints
  1. Primary Key
  2. Autoincrement -> For integer values, this means that the value is automatically filled in and incremented with each row insertion
  3. Unique
  4. Not null
  5. Foreign key -> helps in insert and delete in the table in which the column is foreign key.
  ![alt text](<Screenshot (67).png>)
  6. check(expression) -> validation (Eg: above 18 years can vote)

  ### ALTER TABLE

-  to add new column to a table
  ```sql
  ALTER TABLE mytable
  ADD column DataType OptionalTableConstraint 
  DEFAULT default_value;
  ```
- to remove a column
```sql
ALTER TABLE mytable
DROP column_to_be_deleted;
```
- Rename the table name
```sql
ALTER TABLE mytable
RENAME TO new_table_name;
```

### DROP 
- it also removes the table schema from the database entirely.
```sql
DROP TABLE IF EXISTS mytable;
```

- If you have another table that is dependent on columns in table you are removing (for example, with a FOREIGN KEY dependency) then you will have to either update all dependent tables first to remove the dependent rows or to remove those tables entirely.

## FUNCTIONS

![alt text](<Screenshot (69).png>)

### String Functions
 1. len -> length of string
 2. left -> gives the characters from left
 3. right -> gives characters from right
 4. SubString -> gives the number of characters we have given from the starting position we give
 5. Upper -> converts to UPPERCASE
 6. Lower -> converts to LOWECASE
 7. Ltrim -> deletes the characters or spaces from left
 8. RTrim -> deletes the characters or spaces from right
 9. CharIndex -> gives the index of character we are searching for in the string
 10. Replace -> replaces the character 
 11. Concat -> combines two strings
 12. Replicate -> repeats 
 13. Reverse -> reverses the string

```sql
Select Len('Akshita') as NameLength;
Select left('Akshita',4);
Select right('Akshita',4);
Select SubString('Akshita',2,3);
Select UPPER('Akshita');
Select LOWER('Akshita');
Select LTRIM('  Akshita Mandala');
Select LTRIM('Akshita','ak');
Select RTRIM('Akshita Mandala              ');
Select RTRIM('Akshita',' ta');
Select CHARINDEX('t','Akshita',1);
Select REPLACE('Akshita','t','v');
select CONCAT('Akshita','Mandala');
Select REPLICATE('FunFriday',5) as Namelength;
Select REVERSE('Fun');
```
![alt text](<Screenshot (71).png>)

### MATHEMATICAL FUNCTIONS
1. Abs
2. Power
3. Round
4. Ceiling
5. Floor

```sql
Select ABS(-34);
Select POWER(2,5);
Select ROUND(58.345,2);
Select CEILING(58.345);
Select FLOOR(58.345);
```
![alt text](<Screenshot (72).png>)


### DATE FUNCTIONS

1. GetDate -> gives today date
2. DateAdd -> to add day,month or year to a date
3. DateDiff -> gives the difference between two dates
4. Format
5. DatePart -> retrieves the part from date
```sql
Select GETDATE();
Select DATEADD(DAY,10,GETDATE());
Select DATEPART(YEAR,GETDATE());
Select DATEDIFF(day,'2024-01-01',GETDATE());
Select FORMAT(GETDATE(),'dd/mm/yyyy');
Select FORMAT(GETDATE(),'dd/MMM/yyyy');
```
![alt text](<Screenshot (73)-1.png>)
