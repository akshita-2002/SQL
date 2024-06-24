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


#### Table Constraints -> data integrity (correctness of data , to avoid junk data)
  1. Primary Key
  2. Autoincrement -> For integer values, this means that the value is automatically filled in and incremented with each row insertion
  3. Unique
  4. Not null
  5. Foreign key -> helps in insert and delete in the table in which the column is foreign key.Avoids ghost data.
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
 9. CharIndex -> gives the index of character or word we are searching for in the string
 10. Replace -> replaces the character 
 11. Concat -> combines two strings
 12. Replicate -> repeats 
 13. Reverse -> reverses the string

```sql
Select Len('Akshita') as NameLength;
Select left('Akshita',4);
Select right('Akshita',4);
Select SubString('Akshita',2,3); -- Searching starts from one
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
Select DATEDIFF(Hour,'2024-01-01',GETDATE());
```
![alt text](<Screenshot (73)-1.png>)


### OPERATORS
- there are two diiferent tables employees and departments.

#### All
```sql
-- Task1 : Find all the employees who earn more than all employees in the 'Sales ' department
Select * from employees
WHere Salary > ALL(Select salary 
                   from employees
				   where department_id=(select department_id from departments where department_name='sales')
				   )
```
#### Any
```sql

-- Task2 : Find all the employees who earn more than any employyes in the 'HR' department
Select * 
from employees e 
where salary > 
Any(Select salary from employees where department_id=
                                           (select department_id from departments where department_name='HR'));
```
#### Exists
```sql

-- Task3 : Find all the departments that have at least one employee with a salary greater than $50,000.
-- filters the result if the sub query returns anything
select * 
from departments as o
where  Exists (select department_id from employees as i where salary > 50000 and o.department_id = i.department_id);
```

## SET OPERATIONS

#### INTERSECTION

#### UNION

#### UNION ALL 
- duplicates the common parts
![alt text](<Screenshot (76).png>)

#### EXCEPT 
- A-B 
- B-A
![alt text](<Screenshot (77).png>)

```sql
Select "Name" from Employees
Intersect
Select "Name" from Contractors

Select "Name" from Employees
Union
Select "Name" from Contractors

Select "Name" from Employees
Except
Select "Name" from Contractors

Select "Name" from Employees
Union all
Select "Name" from Contractors

```

#### MULTI JOINS

```sql
Select [Name],ProjectName from Employees as e 
Inner Join Participations as par 
on e.EmployeeID=par.EmployeeID
Inner Join 
Projects as proj
on proj.ProjectID=par.ProjectID
where Name='Alice'
```


#### MULTI LEVEL GROUPING
![alt text](<Screenshot (82).png>)
![alt text](<Screenshot (83).png>)

#### GROUPING SETS
```sql
Select region,product_type,Sum(sales_amount)
From sales_data
Group By GROUPING Sets ((region),(product_type),(region,product_type));
```

#### CUBE vs ROLLUP
##### Cube 
- gives all possible combinations
- gives region,product,(region,product_type),() 
- the empty set returns the sum of all amounts
- 2^n combinations
#### ROLLUP
- we get only three combinations region,(region,product_type) and ()
- (n+1) combinations
![alt text](<Screenshot (85).png>)

# RANKING
Ranking
- 1. Rank
- 2. Dense Rank
- 3. Row_Number
- 4. 

```sql
Select * 
,Rank() OVER (Order By Sales_amount desc) as rankOfSales
,DENSE_RANK() OVER (Order By Sales_amount desc) as DenseRank
,ROW_NUMBER() OVER (Order By Sales_amount desc) as rowRank
from sales_data
```

![alt text](<Screenshot (87).png>)

#### PARTION BY
- to get rank of products according to region , we are doing partioning of region
```sql
Select Region , Sum(sales_amount)as Total_sales , product_type
,DENSE_RANK() OVER (Partition By Region Order by Sum(Sales_amount) Desc) As rank_of_regions
From sales_data
Group By region,product_type
```
![alt text](<Screenshot (89).png>)
#### COMMON TABLE EXPRESSION
- to get a temporary table 
- so that we can perform group by and where on alias names
![alt text](<Screenshot (88).png>)


## ER DIAGRAM
### CARDINALITY

- ONE-ONE RELATIONSHIP => for every value in table 1 there should be only one value in table two
- ONE-MANY RELATIONSHIP
- MANY-MANY RELATIONSHIP


- Schema => Using create statement create tables using entity
- Check is custom validation
- We have to give a name to the constraint 
     - so that we get to know when there is an error which part the error is occuring
     - to update or change the constraint

- to add check constriant
```sql
Alter Table Actor
Add Constraint Ck_Actor Check(
len(name) >0
);
```
- to add auto increment , we use identity as sql doesnt support auto increment
```sql
indentity(1,1);
```
- means increment start from 1 and increments by an increment of 1


### XML-AUTO AND XML-PATH

- to send data from layer to another a common language is required.
- Json is the common language for backend,frontend and database
- XML is the older version of JSON
- XML Auto gives attributes
- XML Path gives keys

```sql
Select *
from Movies
for XML AUTO; --> to covert sql to xml


Select *
from Movies
for XML PATH; --> to convert sql to xml => more specific (valid XML)
```

```sql
Select MovieID,Title,DirectorID
from Movies
for XML PATH ('Movie');
```
- the path gives row by default to change the name to movie use 👆

```sql
Select *
from Movies
for XML PATH ('Movie') , Root('Movies')
```
- to put the whole code in one container use root and to give a name movies 👆

- to get some of them as attributes and others as keys
```sql
Select 
MovieID as [@MovieID],
Title,
DirectorID
from Movies
for XML PATH ('Movie');
```

- to get nested xml
- to get title inside movieInfo
```sql
Select 
MovieID as [@MovieID],
Title as [MovieInfo/Title],
DirectorID
from Movies
for XML PATH ('Movie');
```


#### JSON

- to convert sql to json
- Json path gives the result in array , in this case we can add root
```sql

Select * 
from movies
for JSON Auto;

Select *
From Movies
For JSON PATH;

Select *
FROm movies
FOR JSON PATH , Root
Select *
FROm movies
FOR JSON PATH , Root('Movies')
```
![alt text](<Screenshot (92).png>) 


### TERMS IN SQL

- DATABASE KEYS
  - Primary key
  - Foreign key
  - Candidate key => columns that are eligible to become primary key
  - ALternate key => The keys that are eligible to become primary key other than primary key

     Alternate Key = Candidate key - primary key
    
  - Composite key
  - Super key => group of single or multiple keys which indentifies rows in a table.
  - In super key each column is a primary key
  - in composite key combination of columns is a primary key

     Super Key => Primary Key , Candidate Key , Alternate Key


- CROSS JOIN : each row of one table is multiplied by all rows in other table
![alt text](<Screenshot (95).png>)
![alt text](<Screenshot (97).png>)

- NATURAL JOIN : No need to mention condition to join, same as inner join. Based on cloumn name
```sql
Select * from EMployees
Natural Join Departments
```

- EQUI JOIN : same as inner join , condition must be presented.The condition is always equal to(=). Equi Join is not supported in sql server.
```sql
Select * from Emp
EQUI Join Dep
On column_name
```

- SELF JOIN : join with itself
```sql
-- to get actors with more than one role in a  movie
Select role1.MovieId,role2.ActorId,role1.role
   From MovieActors role1
   Inner Join MovieActors role2
   On role1.MovieID=role2.MovieID
   And role1.ActorId=role2.ActorId
   And role1.Role <> role2.Role
``` 


### FORMAT FUNCTIONS
- Convert advantage - can be used for date
- the parameters(101,103,111) are called as stlying code , to style  date 
```sql
Select Convert(int,Avg(sales_amount))as average_sales
from sales_data
group by region;

SELECT CAST(25.65 AS int);
SELECT CONVERT(int,25.67);

Select CONVERT(float,24);
Select (GETDATE());
Select CAST(GETDATE() AS nvarchar );
```

### DECLARING A VARIABLE
```sql
Declare @movie_id Int;
Set @movie_id = 3;

Select * from Movies
Where MovieId = @movie_id;
```


#### CREATING FUNCTION
- returns is used for return data type
- return is used for what to return 
```sql

Create Function dbo.CalcualteAge(@ReleaseDate Int)
Returns int
As 
Begin
   Return Year(GetDate()) - @ReleaseDate;
End;

Select dbo.CalcualteAge(2005);

Select *,dbo.CalcualteAge([Year]) From Movies;	
```


- Limit is not supoorted in sql , use top instead

- OFFSET AND FETCH SHOULD BE USED IN SQL INSTEAD OF LIMIT AND OFFSET
```sql
Select  *,dbo.CalcualteAge([Year]) as Diff_year
From Movies
Order By Diff_year DESC 
OFFSET 3 rows
FETCH NEXT 3 rows ONLY;
```
- to skip first 3 rows and get next 3 rows

#### VIEW
- filter
- doesnt create another table
- virtual table
- when we call view it calls the actual table
- it copies by reference
- Complex statement - create view for easy readability 
- abstraction - to hide the complexity 
```sql
--last decade movies
create view vWLastDecadeMovies   -- vW is for developers to know that it is a view table , if we update movies table the view table will automatically get updated
as
Select MovieID,Title,[YEAR] from Movies
Where [year] Between 2010 AND 2020;

select * from vWLastDecadeMovies;
```
- safety - to hide some rows and columns that are confidential

### CASE
```sql
Select *,
Case When BoxOffice > 10000000000 Then 'BlockBuster'
     When BoxOffice Between 1000000000 AND 10000000000 Then 'Hit'
	 When BoxOffice < 1000000000 Then 'Average'
	 Else 'Flop'
     End as Category
From Movies;
```
### INLINE , MULTI and SCALAR FUNCTIONS

- Scalar Function 
```sql
Create Function dbo.CalculateAgeOfMovie(@MovieID Int)
Returns int
As
Begin
  Declare @age int
  Set @age = (Select Year(GetDate())-ReleaseYear 
              From Movies
			  Where MovieID=@MovieID)
 Return(@age);
End;

Select *, dbo.CalculateAgeOfMovie(MovieID)  as Age
From Movies;
```
- Inline Table-Valued Function
 ```sql
Create Function dbo.GetMoviesByBudgetRange (@MinBudget float , @MaxBudget float)
Returns table
As
	Return (Select * From 
	         Movies
			 Where Budget BETWEEN @MinBudget AND @MaxBudget);
 
 
Select *
FRom dbo.GetMoviesByBudgetRange(60000000,1800000000)
```

- Multi-statement table-valued function
- MTVF -> we can insert ,update and delete the table created inside the MTVF
```sql
--Task: Create a multi-statement table-valued function named dbo.GetTopActorsByMovieCount that returns actors who have acted in more than 2 movies.
Create function dbo.GetTopActorsByMovieCount()
Returns @tablewithactors Table (ActorId int, FullName nvarchar(50))
As
  Begin
   Insert into @tablewithactors
   Select ActorId , CONCAT(FirstName,' ',LastName)
   From Actors
   Where ActorID In (Select ActorID
                     From MovieActors
					 Group By ActorID
					 Having COUNT(*) >2)
 Return
END;

Select *
FROm dbo.GetTopActorsByMovieCount();
```


#### IF-ELSE , WHILE

- if-else 
```sql
Declare @OrderAmount Decimal(10,2) = 1500.00

If @OrderAmount > 1000
Begin
    Print 'Applying 10% discount'
End
Else
Begin
   Print 'No Discount'
End
```
- While
```sql
Declare @Counter Int = 10

While @Counter > 0
Begin 
  Print @Counter
  Set @Counter= @Counter - 1
End
```

### CREATE PROCEDURE

- Multiple dml statements can be used
- multiple select , create statements are used 

```sql
Create Procedure spGetMovie
   @Genre nvarchar(20)
As
Begin
Select * From Movies
    Where Genre = @Genre
End

Exec spGetMovie 'Action'
Execute spGetMovie 'Action'
```

```sql
-- inbuilt store procedure
--sp_helptext -> returns the content inside the function
Exec sp_helptext GetActorsWithMultipleRoles
```

# MONGO DB
- insertion is slow
- retrieval is fast
- Social media apps are read heavy
- indexing - by default sql gives indexing , does grouping
- indexing creates a tree
![alt text](<Screenshot (98)-1.png>)
-  problem with indexing - the more indexing insertion is slower
- table scanner scans the columns with no index for searching
- 