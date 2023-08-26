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
WHERE name LIKE 'C%' AND name LIKE '%ia%'
```

#### 6. Greece has a double e - who has a double o?
#### Find the country that has oo in the name
```SQL 
SELECT name FROM world
WHERE name LIKE '%oo%'
```