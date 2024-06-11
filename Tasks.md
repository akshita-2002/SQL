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