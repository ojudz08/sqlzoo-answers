<p align="right"><a href="https://github.com/ojudz08/sqlzoo-answers/tree/main">Back To Main Page</a></p>

## Using GROUP BY and HAVING Tutorial
### World Country Profile
```
GROUP BY and HAVING
```
By including a GROUP BY clause functions such as SUM and COUNT are applied to groups of items sharing values. When you specify GROUP BY continent the result is that you get only one row for each different value of continent. All the other columns must be "aggregated" by one of SUM, COUNT ...

The HAVING clause allows use to filter the groups which are displayed. The WHERE clause filters rows before the aggregation, the HAVING clause filters after the aggregation.

If a ORDER BY clause is included we can refer to columns by their position.



#### 1. For each continent show the number of countries:
```SQL
SELECT continent, COUNT(name) FROM world
GROUP BY continent
```


#### 2. For each continent show the total population:
```SQL
SELECT continent, SUM(population) FROM world
GROUP BY continent
```


#### 3. WHERE and GROUP BY. The WHERE filter takes place before the aggregating function. 
#### For each relevant continent show the number of countries that has a population of at least 200000000.
```SQL
SELECT continent, COUNT(name) FROM world
WHERE population > 200000000
GROUP BY continent
```


#### 4. GROUP BY and HAVING. The HAVING clause is tested after the GROUP BY. You can test the aggregated values with a HAVING clause.
#### Show the total population of those continents with a total population of at least half a billion.
```SQL
SELECT continent, SUM(population) FROM world
GROUP BY continent
HAVING SUM(population) >= 500000000
```

<p align="right"><a href="#top">Back To Top</a></p>
