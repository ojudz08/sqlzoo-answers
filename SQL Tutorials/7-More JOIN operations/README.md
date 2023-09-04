<p align="right"><a href="https://github.com/ojudz08/sqlzoo-answers/tree/main">Back To Main Page</a></p>

## More JOIN operations Tutorial
This tutorial introduces the notion of a join. The database consists of three tables movie, actor and casting .

[More details about the database](https://sqlzoo.net/wiki/More_details_about_the_database.)

![Movie Actor Casting](https://github.com/ojudz08/sqlzoo-answers/blob/main/img/more_join_operation.png)


### 1962 movies
#### 1. List the films where the yr is 1962 [Show id, title]
```SQL
SELECT id, title FROM movie
WHERE yr = 1962
```


### When was Citizen Kane released?
#### 2. Give year of 'Citizen Kane'.
```SQL
SELECT yr FROM movie
WHERE title = 'Citizen Kane'
```


### Star Trek movies
#### 3. List all of the Star Trek movies, include the id, title and yr (all of these movies include the words Star Trek in the title). Order results by year.
```SQL
SELECT id, title, yr FROM movie
WHERE title LIKE '%Star Trek%'
ORDER BY yr
```


### id for actor Glenn Close
#### 4. What id number does the actor 'Glenn Close' have?
```SQL
SELECT id FROM actor
WHERE name = 'Glenn Close'
```


### id for Casablanca
#### 5. What is the id of the film 'Casablanca'
```SQL
SELECT id FROM movie
WHERE title = 'Casablanca'
```


#### [Get to the point](https://github.com/ojudz08/sqlzoo-answers/tree/main/References/Get%20to%20the%20point)
### Cast list for Casablanca
#### 6. Obtain the cast list for 'Casablanca'
What is a cast list? The cast list is the names of the actors who were in the movie.
#### Use movieid=11768, (or whatever value you got from the previous question)
```SQL
SELECT name FROM actor
JOIN casting ON actorid = id
WHERE movieid = 11768
```


### Alien cast list
#### 7. Alien cast list
```SQL
SELECT a.name FROM casting c
JOIN actor a ON a.id = c.actorid
JOIN movie m ON m.id = c.movieid
WHERE m.title = 'Alien'
```


### Harrison Ford movies
#### 8. List the films in which 'Harrison Ford' has appeared
```SQL
SELECT m.title FROM casting c
JOIN actor a ON a.id = c.actorid
JOIN movie m ON m.id = c.movieid
WHERE a.name = 'Harrison Ford'
```


### Harrison Ford as a supporting actor
#### 9. List the films where 'Harrison Ford' has appeared - but not in the starring role. [Note: the ord field of casting gives the position of the actor. If ord=1 then this actor is in the starring role]
```SQL
SELECT m.title FROM casting c
JOIN actor a ON a.id = c.actorid
JOIN movie m ON m.id = c.movieid
WHERE a.name = 'Harrison Ford' AND c.ord <> 1
```


### Lead actors in 1962 movies
#### 10. List the films together with the leading star for all 1962 films.
```SQL
SELECT m.title, a.name FROM casting c
JOIN actor a ON a.id = c.actorid
JOIN movie m ON m.id = c.movieid
WHERE c.ord = 1 AND m.yr = 1962
```

## Harder Questions
### Busy years for Rock Hudson
#### 11. Which were the busiest years for 'Rock Hudson', show the year and the number of movies he made each year for any year in which he made more than 2 movies.
```SQL
SELECT yr, COUNT(title) FROM movie
JOIN casting ON movie.id = movieid
JOIN actor ON actorid = actor.id
WHERE name = 'Rock Hudson'
GROUP BY yr
HAVING COUNT(title) > 2
```


### Lead actor in Julie Andrews movies
#### 12. List the film title and the leading actor for all of the films 'Julie Andrews' played in.
Did you get "Little Miss Marker twice"?
Julie Andrews starred in the 1980 remake of Little Miss Marker and not the original(1934).

Title is not a unique field, create a table of IDs in your subquery
```SQL
SELECT m.title, a.name FROM casting c
JOIN movie m ON (m.id = c.movieid AND c.ord = 1)
JOIN actor a ON a.id = c.actorid
WHERE m.id in (SELECT movieid FROM casting
               WHERE actorid IN ( SELECT id FROM actor WHERE name='Julie Andrews' ) )
```


### Actors with 15 leading roles
#### 13. Obtain a list, in alphabetical order, of actors who've had at least 15 starring roles.
```SQL
SELECT name FROM actor
WHERE id IN (SELECT c.actorid from casting c
             WHERE c.ord = 1
             GROUP BY c.actorid
             HAVING SUM(c.ord) >= 15)
ORDER BY name
```


### Released in the year 1978
#### 14. List the films released in the year 1978 ordered by the number of actors in the cast, then by title.
```SQL
SELECT m.title, COUNT(a.id) n_actors FROM casting c 
JOIN movie m ON m.id = c.movieid
JOIN actor a ON a.id = c.actorid
WHERE m.yr = 1978
GROUP BY m.title
ORDER BY n_actors DESC, m.title
```


### With 'Art Garfunkel'
#### 15. List all the people who have worked with 'Art Garfunkel'.
```SQL
SELECT a.name FROM casting c
JOIN actor a on a.id = c.actorid
WHERE movieid IN (SELECT movieid FROM casting c
                  JOIN actor a ON a.id = c.actorid
                  WHERE a.name = 'Art Garfunkel')
AND a.name <> 'Art Garfunkel'
```

<p align="right"><a href="#top">Back To Top</a></p>
