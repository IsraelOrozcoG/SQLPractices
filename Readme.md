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