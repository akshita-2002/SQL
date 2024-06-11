# STUCTURED QUERY LANGUAGE

- SQL is a query language that communicates with databases.

- SQL can create , update, delete and retrieve data from databases like mySql , Oracle, PostgreSQL...

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

- bcnf => shorter version of 3NF => Every attribute in a table should depend on the key, the whole key.


## JOINS

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
