# Ejercicios de Msyql 

## SqlBolt
<details>

<summary>SQL Lesson 1: SELECT queries 101</summary>

Find the title of each film 
```

SELECT Title FROM movies
```

Find the director of each film 
```

SELECT Director FROM movies
```

Find the title and director of each film 
```

SELECT Title, Director FROM movies
```

Find the title and year of each film 
```

SELECT Title, year FROM movies
```

Find all the information about each film
```

SELECT * FROM movies
```
</details>
<details>

<summary>SQL Lesson 2: Queries with constraints (Pt. 1)</summary>

Find the movie with a row id of 6 
```

SELECT * FROM movies WHERE id = 6;
```
Find the movies released in the years between 2000 and 2010
```

SELECT * FROM movies WHERE year >= 2000 AND year<=2010;
```
Find the movies not released in the years between 2000 and 2010
```

SELECT * FROM movies WHERE NOT( year >= 2000 AND year<=2010);
```
Find the first 5 Pixar movies and their release year
```

SELECT * FROM Movies ORDER BY YEAR ASC LIMIT 0, 6;
```
</details>
<details>

<summary>SQL Lesson 3: Queries with constraints (Pt. 2)</summary>
Find all the Toy Story movies 

```
SELECT Title FROM movies WHERE Title like "Toy Story%"
```
Find all the movies directed by John Lasseter
```
SELECT title, director FROM movies 
WHERE director = "John Lasseter";
```
Find all the movies (and director) not directed by John Lasseter
```
SELECT title, director FROM movies 
WHERE NOT director = "John Lasseter";
```
Find all the WALL-* movies
```
SELECT * FROM movies 
WHERE title  LIKE "WALL%";
```

</details>


<details>

<summary>SQL Lesson 4: Filtering and sorting Query results</summary>

List all directors of Pixar movies (alphabetically), without duplicates

```
SELECT DISTINCT Director FROM movies ORDER BY Director ASC ;
```
List the last four Pixar movies released (ordered from most recent to least)
```
SELECT * FROM movies WHERE year ORDER BY year DESC LIMIT 4;
```
List the first five Pixar movies sorted alphabetically
```
SELECT * FROM movies  ORDER BY Title asc LIMIT 5
```

List the next five Pixar movies sorted alphabetically
```
SELECT * FROM movies  ORDER BY Title asc LIMIT 5 OFFSET 5
```
</details>

<details>

<summary>SQL Review: Simple SELECT Queries</summary>
List all the Canadian cities and their populations

```
SELECT city, country,population FROM north_american_cities WHERE Country="Canada";
```
Order all the cities in the United States by their latitude from north to south

```
SELECT * FROM north_american_cities WHERE Country="United States" ORDER BY Latitude DESC;
```
List all the cities west of Chicago, ordered from west to east

```
SELECT * FROM north_american_cities WHERE Longitude<-87.629798 ORDER BY Longitude ASC;
```
List the two largest cities in Mexico (by population)

```
SELECT * FROM north_american_cities WHERE COUNTRY="Mexico" ORDER BY Population DESC  LIMIT 2 ;
```
List the third and fourth largest cities (by population) in the United States and their population

```
SELECT * FROM north_american_cities WHERE Country ="United States" ORDER BY population DESC LIMIT 2 OFFSET 2 ;
```
</details>


<details>

<summary>SQL Lesson 6: Multi-table queries with JOINs</summary>

Find the domestic and international sales for each movie
```
SELECT Domestic_sales, International_sales,Title
FROM  Boxoffice
JOIN Movies 
    ON id = Movie_id
```
Show the sales numbers for each movie that did better internationally rather than domestically
```
SELECT Domestic_sales, International_sales,Title
FROM  Boxoffice
JOIN Movies 
    ON id = Movie_id
WHERE International_sales>Domestic_sales
```
List all the movies by their ratings in descending order
```
SELECT Domestic_sales, International_sales,Title
FROM  Boxoffice
JOIN Movies 
    ON id = Movie_id
ORDER BY Rating DESC
```
</details>

<details>

<summary>SQL Lesson 7: OUTER JOINs</summary>

Find the list of all buildings that have employees
Find the list of all buildings and their capacity
List all buildings and the distinct employee roles in each building (including empty buildings)


</details>