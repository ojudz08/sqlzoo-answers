## SELECT from Nobel Tutorial
### nobel Nobel Laureates
Practice simple SQL queries on a single table. This tutorial is concerned with a table of Nobel prize winners:
```
nobel(yr, subject, winner)
```
Using the SELECT statement.
| yr | subject | winner |
| :--- | :--- | :--- | 
| 2015 | Chemistry | Aziz Sancar | 
| 2015 | Chemistry | Paul L. Modrich  |
| 2015 | Chemistry | Tomas Lindahl |
| 2015 | Economics | Angus Deaton |
| 2015 | Literature | Svetlana Alexievich |
| ... |  |  |


### Winners from 1950
#### 1. Change the query shown so that it displays Nobel prizes for 1950.
```SQL
SELECT yr, subject, winner FROM nobel
WHERE yr = 1950
```


### 1962 Literature
#### 2. Show who won the 1962 prize for literature.
```SQL
SELECT winner FROM nobel
WHERE yr = 1962
AND subject = 'literature'
```


### Albert Einstein
#### 3. Show the year and subject that won 'Albert Einstein' his prize.
```SQL
SELECT yr, subject FROM nobel
WHERE winner = 'Albert Einstein'
```


### Recent Peace Prizes
#### 4. Give the name of the 'peace' winners since the year 2000, including 2000.
```SQL
SELECT winner FROM nobel
WHERE subject LIKE '%peace%'
AND yr >= 2000
```


### Literature in the 1980's
#### 5. Show all details (yr, subject, winner) of the literature prize winners for 1980 to 1989 inclusive.
```SQL
SELECT * FROM nobel
WHERE subject = 'literature'
AND (yr BETWEEN 1980 and 1989)
```


### Only Presidents
#### 6. Show all details of the presidential winners:
- Theodore Roosevelt
- Thomas Woodrow Wilson
- Jimmy Carter
- Barack Obama
```SQL
SELECT * FROM nobel
WHERE winner in ('Theodore Roosevelt',
                 'Woodrow Wilson',
                 'Jimmy Carter',
                 'Barack Obama')
```


### John
#### 7. Show the winners with first name John
```SQL
SELECT winner FROM nobel
WHERE winner LIKE 'john%'
```


### Chemistry and Physics from different years
#### 8. Show the year, subject, and name of physics winners for 1980 together with the chemistry winners for 1984.
```SQL
SELECT yr, subject, winner FROM nobel
WHERE (subject = 'physics' AND yr = 1980)
OR (subject = 'chemistry' AND yr = 1984)
```


### Exclude Chemists and Medics
#### 9. Show the year, subject, and name of winners for 1980 excluding chemistry and medicine
```SQL
SELECT yr, subject, winner FROM nobel
WHERE yr = 1980 AND (subject <> 'chemistry' AND subject <> 'medicine')
```


### Early Medicine, Late Literature
#### 10. Show year, subject, and name of people who won a 'Medicine' prize in an early year (before 1910, not including 1910) together with winners of a 'Literature' prize in a later year (after 2004, including 2004)
```SQL
SELECT yr, subject, winner FROM nobel
WHERE (subject = 'medicine' AND yr < 1910)
OR (subject = 'literature' AND yr >= 2004)
```


## Harder Questions
### Umlaut
#### 11. Find all details of the prize won by PETER GRÜNBERG
```SQL
SELECT * FROM nobel
WHERE winner = 'PETER GRÜNBERG'
```


### Apostrophe
#### 12. Find all details of the prize won by EUGENE O'NEILL
```SQL
SELECT * FROM nobel
WHERE winner = 'EUGENE O''NEILL'
```


### Knights of the realm
#### 13. Knights in order
#### List the winners, year and subject where the winner starts with Sir. Show the the most recent first, then by name order.
```SQL
SELECT winner, yr, subject FROM nobel
WHERE winner LIKE 'Sir%'
ORDER BY yr DESC;
```


### Chemistry and Physics last
#### 14. The expression subject IN ('chemistry','physics') can be used as a value - it will be 0 or 1.
#### Show the 1984 winners and subject ordered by subject and winner name; but list chemistry and physics last.
```SQL
SELECT winner, subject FROM nobel
WHERE yr = 1984
ORDER BY subject IN ('physics','chemistry') ASC, subject, winner
```