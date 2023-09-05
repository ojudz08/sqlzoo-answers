<p align="right"><a href="https://github.com/ojudz08/sqlzoo-answers/tree/main">Back To Main Page</a></p>

## BBC Quiz
| name | continent | area | population | gdp |
| :--- | :--- | :--- | :--- | :--- |
| Afghanistan | South Asia | 652230 | 25500100 | 20343000000 |
| Albania | Europe |  |  |  |
| Algeria | Middle East |  |  |  |
| Andorra | Europe |  |  |  |
| Brazil | South America |  |  |  |
| ... |  |  |  |  |

## Quiz and Answers
#### 1. Select the code which gives the name of countries beginning with U
##### ANSWER
```SQL
SELECT name FROM world
WHERE name LIKE 'U%'
```


#### 2. Select the code which shows just the population of United Kingdom?
##### ANSWER
```SQL
SELECT population FROM world
WHERE name = 'United Kingdom'
```


#### 3. Select the answer which shows the problem with this SQL code - the intended result should be the continent of France:
```SQL
SELECT continent FROM world 
WHERE 'name' = 'France'
```
##### ANSWER
```
'name' should be name
```


#### 4. Select the result that would be obtained from the following code:
```SQL
SELECT name, population / 10 FROM world 
WHERE population < 10000
```
##### ANSWER
| name | population/10 |
| :--- | :--- | 
| Nauru | 990 |


#### 5. Select the code which would reveal the name and population of countries in Europe and Asia
##### ANSWER
```SQL
SELECT name, population FROM world
WHERE continent IN ('Europe', 'Asia')
```


#### 6. Select the code which would give two rows
##### ANSWER
```SQL
SELECT name FROM world
WHERE name IN ('Cuba', 'Togo')
```


#### 7. Select the result that would be obtained from this code:
```SQL
SELECT name FROM world
WHERE continent = 'South America'
AND population > 40000000
```
##### ANSWER
| name |
| :--- | 
| Brazil |
| Colombia |


<p align="right"><a href="#top">Back To Top</a></p>
