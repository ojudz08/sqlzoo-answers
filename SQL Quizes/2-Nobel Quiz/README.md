<p align="right"><a href="https://github.com/ojudz08/sqlzoo-answers/tree/main">Back To Main Page</a></p>

## Nobel Quiz
| yr | subject | winner |
| :--- | :--- | :--- |
| 1960 | Chemistry | Willard F. Libby |
| 1960 | Literature | Saint-John Perse |
| 1960 | Medicine | Sir Frank Macfarlane Burnet |
| 1960 | Medicine | Peter Medawar |
| 1960 | Physics | Donald A. Glaser |
| ... |  |  |

## Quiz and Answers
#### 1. Pick the code which shows the name of winner's names beginning with C and ending in n
##### ANSWER
```SQL
SELECT winner FROM nobel
WHERE winner LIKE 'C%' AND winner LIKE '%n'
```


#### 2. Select the code that shows how many Chemistry awards were given between 1950 and 1960
##### ANSWER
```SQL
SELECT COUNT(subject) FROM nobel
WHERE subject = 'Chemistry'
AND yr BETWEEN 1950 and 1960
```


#### 3. Pick the code that shows the amount of years where no Medicine awards were given
##### ANSWER
```SQL
SELECT COUNT(DISTINCT yr) FROM nobel
WHERE yr NOT IN (SELECT DISTINCT yr FROM nobel 
                 WHERE subject = 'Medicine')
```


#### 4. Select the result that would be obtained from the following code:
```SQL
SELECT subject, winner FROM nobel WHERE winner LIKE 'Sir%' AND yr LIKE '196%'
```
##### ANSWER
| subject | winner |
| :--- | :--- |
| Medicine | Sir John Eccles |
| Medicine | Sir Frank Macfarlane Burnet |


#### 5. Select the code which would show the year when neither a Physics or Chemistry award was given
##### ANSWER
```SQL
SELECT yr FROM nobel
WHERE yr NOT IN (SELECT yr FROM nobel
                 WHERE subject IN ('Chemistry','Physics'))
```


#### 6. Select the code which shows the years when a Medicine award was given but no Peace or Literature award was
##### ANSWER
```SQL
SELECT DISTINCT yr FROM nobel
 WHERE subject='Medicine' 
   AND yr NOT IN(SELECT yr FROM nobel 
                  WHERE subject='Literature')
   AND yr NOT IN (SELECT yr FROM nobel
                   WHERE subject='Peace')
```



#### 7. Pick the result that would be obtained from the following code:
```SQL
SELECT subject, COUNT(subject) FROM nobel 
WHERE yr ='1960' 
GROUP BY subject
```
##### ANSWER
| subject | COUNT(subject) |
| :--- | :--- |
| Chemistry | 1 |
| Literature | 1 |
| Medicine | 2 |
| Peace | 1 |
| Physics | 1 |


<p align="right"><a href="#top">Back To Top</a></p>
