<p align="right"><a href="https://github.com/ojudz08/sqlzoo-answers/tree/main">Back To Main Page</a></p>

## SELECT within SELECT Tutorial
### Nobel Laureates
This tutorial looks at how we can use SELECT statements within SELECT statements to perform more complex queries.
Using the nested SELECT statement.
| name | continet | area | population | gdp |
| :--- | :--- | :--- | :--- | :--- |
| Afghanistan | Asia | 652230 | 25500100 | 20343000000 |
| Albania | Europe |  |  |  |
| Algeria | Africa |  |  |  |
| Andorra | Europe |  |  |  |
| Angola | Africa |  |  |  |
| ... |  |  |  |  |


### Bigger than Russia
#### 1. List each country name where the population is larger than that of 'Russia'.
```
world(name, continent, area, population, gdp)
```
```SQL
SELECT name FROM world
WHERE population > (SELECT population FROM world
                    WHERE name = 'Russia')
```


### Richer than UK
#### 2. Show the countries in Europe with a per capita GDP greater than 'United Kingdom'
per capita GDP = gdp / population
```SQL
SELECT name FROM world
WHERE gdp/population > (SELECT gdp/population FROM world
                        WHERE name = 'United Kingdom')
AND continent = 'Europe' 
```


### Neighbours of Argentina and Australia
#### 3. List the name and continent of countries in the continents containing either Argentina or Australia. Order by name of the country.
```SQL
SELECT name, continent FROM world
WHERE continent IN (SELECT continent FROM world
                    WHERE name IN ('Argentina', 'Australia')) 
```


### Between Canada and Poland
#### 4. Which country has a population that is more than United Kingdom but less than Germany? Show the name and the population.
```SQL
SELECT name, population FROM world
WHERE population > (SELECT population FROM world
                    WHERE name = 'United Kingdom')
AND population < (SELECT population FROM world
                  WHERE name = 'Germany')
```


### Percentages of Germany
#### 5. Germany (population 80 million) has the largest population of the countries in Europe. Austria (population 8.5 million) has 11% of the population of Germany.
#### Show the name and the population of each country in Europe. Show the population as a percentage of the population of Germany.
#### The format should be Name, Percentage for example:
| name | percentage |
| :--- | :--- |
| Albania | 3% |
| Andorra | 0% |
| Austria | 11% |
| ... |  |

Decimal Places: Use the function ROUND to remove the decimal places.

Percent Symbol %: Use the function CONCAT to add the percentage symbol.
```SQL
SELECT name, CONCAT(ROUND((population/(SELECT population FROM world
                                       WHERE name = 'GERMANY'))*100, 0), '%') AS percentage
FROM world
WHERE continent = 'Europe' 
```


### Bigger than every country in Europe
[To get a well rounded view of the important features of SQL you should move on to the next tutorial concerning aggregates.](https://sqlzoo.net/wiki/SUM_and_COUNT)

To gain an absurdly detailed view of one insignificant feature of the language, read on.

We can use the word ALL to allow >= or > or < or <=to act over a list. For example, you can find the largest country in the world, by population with this query:

```SQL
SELECT name FROM world
WHERE population >= ALL (SELECT population FROM world
                         WHERE population>0)
```

#### 6. Which countries have a GDP greater than every country in Europe? [Give the name only.] (Some countries may have NULL gdp values)
```SQL
SELECT name FROM world
WHERE gdp >= ALL(SELECT gdp FROM world
                 WHERE continent = 'Europe' AND gdp > 0)
AND continent <> 'Europe'
```


### Largest in each continent
We can refer to values in the outer SELECT within the inner SELECT. We can name the tables so that we can tell the difference between the inner and outer versions.
#### 7. Find the largest country (by area) in each continent, show the continent, the name and the area:
```SQL
SELECT continent, name, area FROM world x
WHERE area >= ALL (SELECT area FROM world y
                   WHERE y.continent = x.continent
                   AND population > 0) 
```
The above example is known as a correlated or synchronized sub-query.


### First country of each continent (alphabetically)
#### 8. List each continent and the name of the country that comes first alphabetically.
```SQL
SELECT continent, name FROM world x
WHERE name = (SELECT name FROM world
              WHERE continent = x.continent
              ORDER BY continent, name
              LIMIT 1)
```


### Difficult Questions That Utilize Techniques Not Covered In Prior Sections
#### 9. Find the continents where all countries have a population <= 25000000. Then find the names of the countries associated with these continents. Show name, continent and population.
```SQL
SELECT name, continent, population FROM world x
WHERE 25000000 >= ALL (SELECT population FROM world y
		       WHERE x.continent = y.continent
                       AND y.population>0)
```


### Three time bigger
#### 10. Three time bigger
```SQL
SELECT name, continent FROM world x
WHERE population >= ALL (SELECT population*3
                         FROM world y
                         WHERE x.continent = y.continent
                         and y.name != x.name) 
```

<p align="right"><a href="#top">Back To Top</a></p>
