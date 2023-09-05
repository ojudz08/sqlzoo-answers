## Window LAG Tutorial

### COVID-19 Data
Notes on the data: This data was assembled based on work done by Rodrigo Pombo based on John Hopkins University, based on World Health Organisation. The data was assembled 21st April 2020 - there are no plans to keep this data set up to date.

### Window Function
The SQL Window functions include LAG, LEAD, RANK and NTILE. These functions operate over a "window" of rows - typically these are rows in the table that are in some sense adjacent.

### Introducing the covid table
#### 1. The example uses a WHERE clause to show the cases in 'Italy' in March 2020.
#### Modify the query to show data from Spain
```SQL
SELECT name, DAY(whn), confirmed, deaths, recovered FROM covid
WHERE name = 'spain'
AND MONTH(whn) = 3
ORDER BY whn
```


### Introducing the LAG function
----
Note for MySQL: If you are using the MariaDB engine you will hit the bug https://jira.mariadb.org/browse/MDEV-23866
- You can use the Microsoft SQL Server engine instead
- You can include this line before each query:

```SQL
SET @@sql_mode='ANSI';
```
#### 2. The LAG function is used to show data from the preceding row or the table. When lining up rows the data is partitioned by country name and ordered by the data whn. That means that only data from Italy is considered.

#### Modify the query to show confirmed for the day before.
```SQL
SELECT name, DAY(whn), confirmed, LAG(confirmed, 1) OVER (PARTITION BY name ORDER BY whn) FROM covid
WHERE name = 'Italy'
AND MONTH(whn) = 3
ORDER BY whn
```

### LAG Operation
----
Here is the correct query showing the cases for the day before:
```SQL
SELECT name, DAY(whn), confirmed,
   LAG(confirmed, 1) OVER (partition by name ORDER BY whn) AS lag
FROM covid
WHERE name = 'Italy'
AND MONTH(whn) = 3
ORDER BY whn
```
Notice how the values in the LAG column match the value of the row diagonally above and to the left.

| name | Day(whn) | confirmed | dbf |
| :-- | :-- | :-- | :-- |
| Italy | 1 | 1694 | null |
| Italy | 2 | 2036 | 1694 |
| Italy | 3 | 2502 | 2036 |
| Italy | 4 | 3089 | 2502 |
| Italy | 5 | 3858 | 3089 |
| Italy | 6 | 4636 | 3858 |
| Italy | 7 | 5883 | 4636 |
| Italy | 8 | 7375 | 5883 |
| Italy | 9 | 9172 | 7375 |
| Italy | 10 | 10149 | 9172 |
| ... | | | |

### Number of new cases
#### 3. The number of confirmed case is cumulative - but we can use LAG to recover the number of new cases reported for each day.

#### Show the number of new cases for each day, for Italy, for March.
```SQL
SELECT name, DAY(whn), Confirmed - Lag(confirmed, 1) OVER (PARTITION BY name ORDER BY whn) As new FROM covid
WHERE name = 'Italy'
AND MONTH(whn) = 3
ORDER BY whn
```


### Weekly changes
#### 4. The data gathered are necessarily estimates and are inaccurate. However by taking a longer time span we can mitigate some of the effects.

#### You can filter the data to view only Monday's figures WHERE WEEKDAY(whn) = 0.

#### Show the number of new cases in Italy for each week in 2020 - show Monday only.
```SQL
SELECT [ANSWER HERE] 
```


### LAG using a JOIN
#### 5. You can JOIN a table using DATE arithmetic. This will give different results if data is missing.

#### Show the number of new cases in Italy for each week - show Monday only.

#### In the sample query we JOIN this week tw with last week lw using the DATE_ADD function.
```SQL
SELECT tw.name, DATE_FORMAT(tw.whn, '%Y-%m-%d'), tw.confirmed - lw.confirmed AS new FROM covid tw
LEFT JOIN covid lw ON DATE_ADD(lw.whn, INTERVAL 1 WEEK) = tw.whn
AND tw.name = lw.name
WHERE tw.name = 'Italy'
AND WEEKDAY(tw.whn) = 0
ORDER BY tw.whn
```


### RANK()
#### 6. This query shows the number of confirmed cases together with the world ranking for cases for the date '2020-04-20'. The number of COVID deaths is also shown.

#### United States has the highest number, Spain is number 2...

#### Notice that while Spain has the second highest confirmed cases, Italy has the second highest number of deaths due to the virus.

#### Add a column to show the ranking for the number of deaths due to COVID.
```SQL
SELECT name, confirmed, RANK() OVER (ORDER BY confirmed DESC) AS rc, deaths, RANK() OVER (ORDER BY deaths DESC) AS rd FROM covid
WHERE whn = '2020-04-20'
ORDER BY confirmed DESC
```


### Infection rate
#### 7. This query includes a JOIN t the world table so we can access the total population of each country and calculate infection rates (in cases per 100,000).

#### Show the infection rate ranking for each country. Only include countries with a population of at least 10 million.
```SQL
SELECT [ANSWER HERE] 
```


### Turning the corner
#### 8. For each country that has had at last 1000 new cases in a single day, show the date of the peak number of new cases.
```SQL
SELECT [ANSWER HERE] 
```