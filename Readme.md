# Ejercicios de Msyql 
<details>
<summary><strong>SqlBolt</strong> </summary>
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
```
SELECT DISTINCT Building FROM Employees;
```
Find the list of all buildings and their capacity
```
SELECT * FROM Buildings;
```
List all buildings and the distinct employee roles in each building (including empty buildings)
```
SELECT DISTINCT building_name, role 
FROM Buildings 
  LEFT JOIN Employees
    ON Building_name = Building;
```
</details>

<details>

<summary>SQL Lesson 8: A short note on NULLs</summary>

Find the name and role of all employees who have not been assigned to a building
```

SELECT *
FROM Employees
WHERE Building IS NULL
```
Find the names of the buildings that hold no employees
```
SELECT DISTINCT Building_name
FROM Buildings 
  LEFT JOIN Employees
    ON Building_name = Building
WHERE Role IS NULL;
```
</details>

<details>

<summary>SQL Lesson 9: Queries with expressions</summary>

List all movies and their combined sales in millions of dollars

List all movies and their ratings in percent

List all movies that were released on even number years

</details>

<details>
<summary>SQL Lesson 10: Queries with aggregates (Pt. 1)</summary>

Find the longest time that an employee has been at the studio
```
SELECT MAX(Years_employed) as Longest_Time FROM employees;
```
For each role, find the average number of years employed by employees in that role
```
SELECT AVG(Years_employed) as Average_years_employed,Role FROM employees
GROUP BY Role;
```
Find the total number of employee years worked in each building
```
SELECT Building, SUM(Years_employed) as Total_years_employed
FROM employees
GROUP BY Building;
```
</details>

<details>
<summary>SQL Lesson 11: Queries with aggregates (Pt. 2)</summary>
Find the number of Artists in the studio (without a HAVING clause)

```
SELECT Role, COUNT(*) as Artists
FROM Employees
WHERE role = "Artist";
```
Find the number of Employees of each role in the studio
```
SELECT Role, COUNT(*)
FROM Employees
GROUP BY Role;
```
Find the total number of years employed by all Engineers

```
SELECT Role, SUM(years_employed)
FROM Employees
GROUP BY Role
HAVING Role = "Engineer";
```

</details>

<details>
<summary>SQL Lesson 12: Order of execution of a Query</summary>

Find the number of movies each director has directed

```
SELECT Director, COUNT(id) as Quantity_directed_movies
FROM Movies
GROUP BY Director;
```

Find the total domestic and international sales that can be attributed to each director

```
SELECT Director, SUM(Domestic_sales + International_sales) as Domestic_and_International_Sales
FROM Movies
    INNER JOIN boxoffice
        ON Movies.id = Boxoffice.movie_id
GROUP BY director;
```
</details>

<details>
<summary>SQL Lesson 13: Inserting rows</summary>

Add the studio's new production, Toy Story 4 to the list of movies (you can use any director)

```
INSERT INTO movies VALUES (15, "Toy Story 4", "John Lasseter", 2015, 90);
```
Toy Story 4 has been released to critical acclaim! It had a rating of 8.7, and made 340 million domestically and 270 million internationally. Add the record to the BoxOffice table.

```
INSERT INTO BoxOffice
(movie_id, rating, Domestic_sales, International_sales)
VALUES (15, 8.7, 340 000000,270 000000);
```
</details>
</details>

<details>
<summary><strong>Sql_Practice</strong> </summary>
<details>
<summary>  Show first name, last name, and gender of patients whose gender is 'M'</summary>

```
SELECT first_name, last_name, gender 
FROM patients 
WHERE gender = 'M';
```
</details>
</details>