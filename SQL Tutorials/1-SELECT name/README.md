## SELECT names
| name | continet |
| :--- | :--- |
| Afghanistan | Asia | 
| Albania | Europe |
| Algeria | Africa |
| Andorra | Europe |
| Angola | Africa |

## Pattern Matching Strings
This tutorial uses the LIKE operator to check names. Sample SQL query below uses the world table
#### 1. You can use  WHERE name LIKE 'B%' to find the countries that start with "B".
- The % is a wild-card it can match any characters

#### Find the country that start with Y
```SQL
SELECT name FROM world
WHERE name LIKE 'y%'
```


#### 2. Find the countries that end with y
```SQL 
SELECT name FROM world
WHERE name LIKE '%y'
```



#### 3. Luxembourg has an x - so does one other country. List them both.
#### Find the countries that contain the letter x
```SQL 
SELECT name FROM world
WHERE name LIKE '%x%'
```


#### 4. Iceland, Switzerland end with land - but are there others?
#### Find the countries that end with land
```SQL 
SELECT name FROM world
WHERE name LIKE '%land'
```


#### 5. Columbia starts with a C and ends with ia - there are two more like this.
#### Find the countries that start with C and end with ia
```SQL 
SELECT name FROM world
WHERE name LIKE 'c%' AND name LIKE '%ia%'
```

#### 6. Greece has a double e - who has a double o?
#### Find the country that has oo in the name
```SQL 
SELECT name FROM world
WHERE name LIKE '%oo%'
```


#### 7. Bahamas has three a - who else?
#### Find the countries that have three or more a in the name
```SQL 
SELECT name FROM world
WHERE name LIKE '%a%a%a%'
```


#### 8. India and Angola have an n as the second character. You can use the underscore as a single character wildcard.
```SQL
SELECT name FROM world WHERE name LIKE '_n%'
ORDER BY name
```
#### Find the countries that have "t" as the second character.
```SQL 
SELECT name FROM world
WHERE name LIKE '_t%'
ORDER BY name
```


#### 9. Lesotho and Moldova both have two "o" characters separated by two other characters.

#### Find the countries that have two "o" characters separated by two others.
```SQL 
SELECT name FROM world
WHERE name LIKE '%o__o%'
```


#### 10. Cuba and Togo have four characters names.
#### Find the countries that have exactly four characters.
```SQL 
SELECT name FROM world
WHERE LENGTH(name) = 4
```



### Harder Questions
These questions were optional

#### 11. The capital of Luxembourg is Luxembourg. Show all the countries where the capital is the same as the name of the country
#### Find the country where the name is the capital city.
```SQL 
SELECT name FROM world
WHERE name = capital
```


#### 12. The capital of Mexico is Mexico City. Show all the countries where the capital has the country together with the word "City".
#### Find the country where the capital is the country plus "City".
```SQL 
SELECT name FROM world
WHERE concat(name, ' City') = capital
```