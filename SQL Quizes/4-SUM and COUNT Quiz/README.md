<p align="right"><a href="https://github.com/ojudz08/sqlzoo-answers/tree/main">Back To Main Page</a></p>


## SUM and COUNT Quiz
| name | continent | area | population | gdp |
| :--- | :--- | :--- | :--- | :--- |
| Afghanistan | South Asia | 652230 | 25500100 | 20343000000 |
| Albania | Europe |  |  |  |
| Algeria | Middle East |  |  |  |
| Andorra | Europe |  |  |  |
| Brazil | South America |  |  |  |
| ... |  |  |  |  |

## Quiz and Answers
#### 1. Select the statement that shows the sum of population of all countries in 'Europe'
##### ANSWER
```SQL
SELECT SUM(population) FROM bbc WHERE region = 'Europe'
```


#### 2. Select the statement that shows the number of countries with population smaller than 150000
##### ANSWER
```SQL
SELECT COUNT(name) FROM bbc WHERE population < 150000
```


#### 3. Select the list of core SQL aggregate functions
##### ANSWER
```
AVG(), COUNT(), MAX(), MIN(), SUM()
```


#### 4. Select the result that would be obtained from the following code:
```SQL
SELECT region, SUM(area)FROM bbc 
WHERE SUM(area) > 15000000 
GROUP BY region
```
##### ANSWER
```
No result due to invalid use of the WHERE function
```


#### 5. Select the statement that shows the average population of 'Poland', 'Germany' and 'Denmark'
##### ANSWER
```SQL
SELECT AVG(population) FROM bbc
WHERE name IN ('Poland', 'Germany', 'Denmark')
```


#### 6. Select the statement that shows the medium population density of each region
##### ANSWER
```SQL
SELECT region, SUM(population)/SUM(area) AS density FROM bbc
GROUP BY region
```


#### 7. Select the statement that shows the name and population density of the country with the largest population
##### ANSWER
```SQL
SELECT name, population/area AS density FROM bbc
WHERE population = (SELECT MAX(population) FROM bbc)
```


#### 8. Pick the result that would be obtained from the following code:
```SQL
SELECT region, SUM(area) FROM bbc 
GROUP BY region 
HAVING SUM(area) <= 20000000
```
##### ANSWER
| region | sum(area) |
| :--- | :--- | 
| Americas | 732240 |
| Middle East | 13403102 |
| South America | 17740392 |
| South Asia | South Asia |


<p align="right"><a href="#top">Back To Top</a></p>
