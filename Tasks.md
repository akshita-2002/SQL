## Exercise 1 - Tasks

1. Find the title of each film
```sql
Select title From movies;
```

2. Find the director of each film 
```sql
Select Director From movies;
```
3. Find the title and director of each film
```sql
Select Title,Director From movies;
```
4. Find the title and year of each film 
```sql
Select Title,Year From movies;
```
5. Find all the information about each film
```sql
Select * From movies;
```

![alt text](<Screenshot (33).png>)

## Exercise 2 — Tasks

1. Find the movie with a row id of 6 
```sql
Select *
From movies
Where id = 6;
```

2. Find the movies released in the years between 2000 and 2010 
```sql
Select *
From movies
Where year between 2000 AND 2010;
```
3. Find the movies not released in the years between 2000 and 2010 
```sql
SELECT * 
FROM movies 
Where year NOT BETWEEN 2000 AND 2010;
```
4. Find the first 5 Pixar movies and their release year
```sql
SELECT title,year 
FROM movies 
Where id BETWEEN 1 AND 5;
```
![alt text](<Screenshot (35).png>)

## Exercise 3 — Tasks

1. Find all the Toy Story movies 
```sql
SELECT * 
FROM movies 
WHERE director LIKE "Toy Story%";
```
2. Find all the movies directed by John Lasseter
```sql
SELECT * FROM movies 
WHERE director LIKE "John Lasseter%";
```

3. Find all the movies (and director) not directed by John Lasseter 
```sql
SELECT * FROM movies 
WHERE director NOT LIKE "John Lasseter%";
```
4. Find all the WALL-* movies
```sql
SELECT * FROM movies 
WHERE title  LIKE "WALL-_";
```
![alt text](<Screenshot (37).png>)

## Exercise 4 — Tasks

1. List all directors of Pixar movies (alphabetically), without duplicates 
```sql
SELECT DISTINCT Director 
FROM movies
Order By Director ASC;
```

2. List the last four Pixar movies released (ordered from most recent to least)
```sql
SELECT Title 
FROM movies 
Order By Year DESC Limit 4;
```

3. List the first five Pixar movies sorted alphabetically 
```sql
SELECT Title 
FROM movies 
Order By Title ASC Limit 5;
```
4. List the next five Pixar movies sorted alphabetically 
```sql
SELECT title FROM movies
ORDER BY title ASC
LIMIT 5 OFFSET 5;
```

![alt text](<Screenshot (38).png>)

### Review 1 — Tasks
1. List all the Canadian cities and their populations 
```sql
SELECT City,Population 
FROM north_american_cities 
WHERE Country="Canada";
```
2. Order all the cities in the United States by their latitude from north to south 
```sql
SELECT City 
FROM north_american_cities 
WHERE Country="United States" 
ORDER BY latitude DESC;
```
3. List all the cities west of Chicago, ordered from west to east 
```sql
SELECT city, longitude 
FROM north_american_cities
WHERE longitude < -87.629798
ORDER BY longitude ASC;
```
4. List the two largest cities in Mexico (by population)
```sql
SELECT City 
FROM north_american_cities 
Where Country="Mexico" 
ORDER BY Population DESC LIMIT 2;
```

5. List the third and fourth largest cities (by population) in the United States and their population
```sql
SELECT City 
FROM north_american_cities 
Where Country="United States" 
ORDER BY Population DESC LIMIT 2 OFFSET 2;
```

![alt text](<Screenshot (39).png>)

### Exercise 6 — Tasks
1. Find the domestic and international sales for each movie 
```sql
SELECT * 
FROM movies
INNER JOIN Boxoffice ON Movies.Id==Boxoffice.Movie_id; 
```

2. Show the sales numbers for each movie that did better internationally rather than domestically 
```sql
SELECT * 
FROM movies 
INNER JOIN Boxoffice ON Movies.Id==Boxoffice.Movie_id 
WHERE International_sales>Domestic_sales; 
```

3.List all the movies by their ratings in descending order 
```sql
SELECT *
FROM movies 
INNER JOIN Boxoffice ON Movies.Id==Boxoffice.Movie_id
ORDER BY Boxoffice.Rating DESC; 
```

### Exercise 7 — Tasks
1. Find the list of all buildings that have employees 
```sql
SELECT DISTINCT building FROM employees;
```
2. Find the list of all buildings and their capacity
```sql
SELECT * FROM buildings;
```
3. List all buildings and the distinct employee roles in each building (including empty buildings) 
```sql
SELECT DISTINCT building_name, role 
FROM buildings 
LEFT JOIN employees ON building_name = building;
```
![alt text](<Screenshot (54).png>)

### Exercise 8 — Tasks

1. Find the name and role of all employees who have not been assigned to a building 
```sql
SELECT * 
FROM employees 
WHERE Building IS NULL;
```
2. Find the names of the buildings that hold no employees 
```sql
SELECT * FROM Buildings 
Left join Employees on Building_name==Building 
WHERE Name IS NULL;
```

![alt text](<Screenshot (55).png>)

### Exercise 9 — Tasks
1. List all movies and their combined sales in millions of dollars
```sql
SELECT title,(Domestic_sales+International_sales)/1000000
FROM Boxoffice 
inner join movies on id==movie_id;
```

2. List all movies and their ratings in percent 
```sql
SELECT title,Rating*10 
FROM Boxoffice 
inner join movies on id==movie_id;
```

3. List all movies that were released on even number years 
```sql
SELECT * 
FROM Movies 
Where Year%2==0;
```

![alt text](<Screenshot (56).png>)

## Exercise 10 — Tasks
1. Find the longest time that an employee has been at the studio
```sql
SELECT * 
FROM employees 
Order by Years_employed DESC limit 1;
```
2. For each role, find the average number of years employed by employees in that role
```sql
SELECT role,Avg(Years_employed) 
From Employees 
Group BY Role
```
3. Find the total number of employee years worked in each building 
```sql
Select Building,sum(Years_employed) 
From Employees 
Group By Building
```
![alt text](<Screenshot (57).png>)

## Exercise 11 — Tasks
1. Find the number of Artists in the studio (without a HAVING clause)
```sql
SELECT Count(*) 
FROM employees 
Where Role="Artist";
```
2. Find the number of Employees of each role in the studio 
```sql
Select role,count(name) 
from Employees 
group by role;
```
3. Find the total number of years employed by all Engineers 
```sql
Select sum(Years_employed) 
from Employees 
where role="Engineers";
```

![alt text](<Screenshot (59).png>)

## Exercise 12 — Tasks
1. Find the number of movies each director has directed
```sql
SELECT Director,Count(Title) 
FROM movies 
group by Director;
```
2. Find the total domestic and international sales that can be attributed to each director 
```sql
SELECT Director,sum(Domestic_sales+International_sales) 
FROM movies 
inner join Boxoffice on id==Movie_id group by Director;
```
![alt text](<Screenshot (60).png>)

## Exercise 13 — Tasks
1. Add the studio's new production, Toy Story 4 to the list of movies (you can use any director)
```sql
Insert INTO Movies(Id,Title,Director,Year,Length_minutes) Values(4,"Toy Story 4","John Lasseter",2023,95);
```
2. Toy Story 4 has been released to critical acclaim! It had a rating of 8.7, and made 340 million domestically and 270 million internationally. Add the record to the BoxOffice table. 
```sql
Insert INTO Boxoffice Values(4,8.7,340000000,270000000);
```

![alt text](<Screenshot (61).png>)

### Exercise 14 — Tasks
1. The director for A Bug's Life is incorrect, it was actually directed by John Lasseter 

```sql
Select * From Movies Where id=3;
Update Movies
Set Director = "John Lasseter"
Where Title="A Bug's Life";
```
2. The year that Toy Story 2 was released is incorrect, it was actually released in 1999 
```sql
Select * From Movies Where id=3;
Update Movies
Set Year=1999
Where Title="Toy Story 2";
```
3. Both the title and director for Toy Story 8 is incorrect! The title should be "Toy Story 3" and it was directed by Lee Unkrich 
```sql
Select * from movies where id=11;
Update Movies 
Set Title="Toy Story 3",Director="Lee Unkrich"
Where Title="Toy Story 8";
```

![alt text](<Screenshot (62).png>)

## Exercise 15 — Tasks
1. This database is getting too big, lets remove all movies that were released before 2005.

```sql
SELECT * FROM Movies Where Year<2005;
Delete from Movies
Where Year<2005;
```
2. Andrew Stanton has also left the studio, so please remove all movies directed by him. 
```sql
Select * from movies where Director="Andrew Stanton";
Delete from movies
Where Director="Andrew Stanton";
```

![](<Screenshot (63).png>)


## Exercise 16 — Tasks
1. Create a new table named Database with the following columns:
– Name A string (text) describing the name of the database
– Version A number (floating point) of the latest version of this database
– Download_count An integer count of the number of times this database was downloaded
This table has no constraints. 
```sql
Create table if not exists Database(Name text, Version Float,Download_count Int);
```
## Exercise 17 — Tasks
1. Add a column named Aspect_ratio with a FLOAT data type to store the aspect-ratio each movie was released in. 
```sql
Alter table Movies
add Aspect_ratio float;
```
2. Add another column named Language with a TEXT data type to store the language that the movie was released in. Ensure that the default for this language is English.

```sql
Alter table Movies
Add Language Text Default English;
```