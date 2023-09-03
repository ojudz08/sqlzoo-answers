## SELECT basics Tutorial
<p align="left"><a>## SELECT basics Tutorial</a></p>
<p align="right">(<a href="https://github.com/ojudz08/sqlzoo-answers/tree/main">back to main page</a>)</p>

| name | continet | area | population | gdp |
| :--- | :--- | :--- | :--- | :--- |
| Afghanistan | Asia | 652230 | 25500100 | 20343000000 |
| Albania | Europe |  |  |  |
| Algeria | Africa |  |  |  |
| Andorra | Europe |  |  |  |
| Angola | Africa |  |  |  |
| ... |  |  |  |  |

## Exercises and Answers
#### 1. Introducing the world table countries
Show the population of Germany
```SQL
SELECT population FROM world
WHERE name = 'Germany'
```

#### 2. Scandinavia
Show the name and the population for Sweden, Norway and Denmark
```SQL
SELECT name, population FROM world
WHERE name IN ('Sweden', 'Norway', 'Denmark')
```

#### 3. Just the right size
Show the country and area that has an area between 200,000 and 250,000
```SQL
SELECT name, area FROM world
WHERE area BETWEEN 200000 AND 250000
```
