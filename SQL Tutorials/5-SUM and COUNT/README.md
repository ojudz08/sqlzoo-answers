## SUM and COUNT Tutorial
### World Country Profile: Aggregate fucntions
This tutorial is about aggregate functions such as COUNT, SUM and AVG. An aggregate function takes many values and delivers just one value. For example the function SUM would aggregate the values 2, 4 and 5 to deliver the single value 11.
| name | continet | area | population | gdp |
| :--- | :--- | :--- | :--- | :--- |
| Afghanistan | Asia | 652230 | 25500100 | 20343000000 |
| Albania | Europe |  |  |  |
| Algeria | Africa |  |  |  |
| Andorra | Europe |  |  |  |
| Angola | Africa |  |  |  |
| ... |  |  |  |  |


Look at these references before proceeding to the exercise below.
Using [SUM, Count, MAX, DISTINCT and ORDER BY](https://github.com/ojudz08/sqlzoo-answers/tree/main/References/SUM%2C%20Count%2C%20MAX%2C%20DISTINCT%20and%20ORDER%20BY)

### Total world population
#### 1. Show the total population of the world.
```SQL
SELECT SUM(population)
FROM world
```


### List of continents
#### 2. List all the continents - just once each.
```SQL
SELECT DISTINCT continent FROM world
```


### GDP of Africa
#### 3. Give the total GDP of Africa
```SQL
SELECT SUM(gdp) FROM world
WHERE continent = 'Africa'
```


### Count the big countries
#### 4. How many countries have an area of at least 1000000
```SQL
SELECT COUNT(name) AS Countries_1M_Area FROM world
WHERE area >= 1000000
```


### Baltic states population
#### 5. What is the total population of ('Estonia', 'Latvia', 'Lithuania')
```SQL
SELECT SUM(population) FROM world
WHERE name IN ('Estonia', 'Latvia', 'Lithuania')
```


### Using GROUP BY and HAVING
You may want to look at these examples: Using [GROUP BY and HAVING](https://github.com/ojudz08/sqlzoo-answers/tree/main/References/GROUP%20BY%20and%20HAVING)


### Counting the countries of each continent
#### 6. For each continent show the continent and number of countries.
```SQL
SELECT continent, COUNT(name) FROM world
GROUP BY continent
```

### Counting big countries in each continent
#### 7. For each continent show the continent and number of countries with populations of at least 10 million.
```SQL
SELECT continent, COUNT(name) FROM world
WHERE population >= 10000000
GROUP BY continent
```


### Counting big continents
#### 8. List the continents that have a total population of at least 100 million.
```SQL
SELECT continent FROM world
WHERE population >= 100000000
GROUP BY continent
```