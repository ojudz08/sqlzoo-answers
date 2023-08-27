## Get to the point
### Movie Database: The JOIN

The obvious questions about this database involve all three tables. Who appear in such-and-such a film, or which films has so-and-so appeared in. In fact we can answer some of these questions using nested SELECT statements that have already been covered.

A join allows us to link two tables which have a "common" field. The id field of the actor table is referred to by the actorid field of the casting table. A join of these tables on these fields produces a table which includes all of the attributes of both tables.


### Joining two tables
#### 1. Join casting and actor on actorid/id

The result below gives one row for every element of the casting table which relates to John Hurt. In addition to the actorid we have the name of the actor involved.

```SQL
SELECT * FROM casting
JOIN actor ON casting.actorid=actor.id
WHERE actor.name='John Hurt'
```

### Joining three tables
#### 2. Join casting and actor on actorid/id

The it makes sense to join the above table with the movie table. The obvious field to join on is the movieid field.

```SQL
SELECT * FROM movie
JOIN casting ON movie.id=movieid
JOIN actor   ON actorid=actor.id
WHERE actor.name='John Hurt'
```
