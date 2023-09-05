<p align="right"><a href="https://github.com/ojudz08/sqlzoo-answers/tree/main">Back To Main Page</a></p>

## SELECT Quiz
Some questions concerning basic SQL statements
| name | continet | area | population | gdp |
| :--- | :--- | :--- | :--- | :--- |
| Afghanistan | Asia | 652230 | 25500100 | 20343000000 |
| Albania | Europe |  |  |  |
| Algeria | Africa |  |  |  |
| Andorra | Europe |  |  |  |
| ... |  |  |  |  |

## Quiz and Answers
#### 1. Select the code which produces this table
| name | population |
| :--- | :--- | 
| Bahrain | 1234571 | 
| Swaziland | 1220000 |
| Timor-Leste | 1066409 |

##### ANSWER
```SQL
SELECT name, population FROM world
WHERE population BETWEEN 1000000 AND 1250000
```


#### 2. Pick the result you would obtain from this code:
```SQL
SELECT name, population FROM world
WHERE name LIKE "Al%"
```

##### ANSWER
| name | population |
| :--- | :--- | 
| Albania | 3200000 | 
| Algeria | 32900000 |


#### 3. Select the code which shows the countries that end in A or L
##### ANSWER
```SQL
SELECT name FROM world
WHERE name LIKE '%a' OR name LIKE '%l'
```


#### 4. Pick the result from the query
```SQL
SELECT name, length(name) FROM world
WHERE length(name) = 5 and region = 'Europe'
```

##### ANSWER
| name | length(name) |
| :--- | :---: | 
| Italy | 5 | 
| Malta | 5 |
| Spain | 5 |


#### 5. Pick the result you would obtain from this code:
```SQL
SELECT name, area*2 FROM world WHERE population = 64000
```

##### ANSWER
| name | area*2 |
| :--- | :---: | 
| Andorra | 936 |


#### 6. Select the code that would show the countries with an area larger than 50000 and a population smaller than 10000000
##### ANSWER
```SQL
SELECT name, area, population FROM world
WHERE area > 50000 AND population < 10000000
```


#### 7. Select the code that shows the population density of China, Australia, Nigeria and France
##### ANSWER
```SQL
SELECT name, population/area FROM world
WHERE name IN ('China', 'Nigeria', 'France', 'Australia')
```

<p align="right"><a href="#top">Back To Top</a></p>
