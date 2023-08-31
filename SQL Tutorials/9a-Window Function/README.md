## Window Functions Tutorial

General Elections were held in the UK in 2015 and 2017. Every citizen votes in a constituency. The candidate who gains the most votes becomes MP for that constituency.

All these results are recorded in a table ge

[INSERT TABLE HERE]

### Warming up
#### 1. Show the lastName, party and votes for the constituency 'S14000024' in 2017.
```SQL
SELECT [ANSWER HERE] 
```

### Who won?
#### 2. You can use the RANK function to see the order of the candidates. If you RANK using (ORDER BY votes DESC) then the candidate with the most votes has rank 1.

##### Show the party and RANK for constituency S14000024 in 2017. List the output by party
```SQL
SELECT [ANSWER HERE] 
```

### PARTITION BY
#### 3. The 2015 election is a different PARTITION to the 2017 election. We only care about the order of votes for each year.
#### Use PARTITION to show the ranking of each party in S14000021 in each year. Include yr, party, votes and ranking (the party with the most votes is 1).
```SQL
SELECT [ANSWER HERE] 
```

### Edinburgh Constituency
#### 4. Edinburgh constituencies are numbered S14000021 to S14000026.
#### Use PARTITION BY constituency to show the ranking of each party in Edinburgh in 2017. Order your results so the winners are shown first, then ordered by constituency.
```SQL
SELECT [ANSWER HERE] 
```

### Winners Only
#### 5. You can use SELECT within SELECT to pick out only the winners in Edinburgh.
#### Show the parties that won for each Edinburgh constituency in 2017.
```SQL
SELECT [ANSWER HERE] 
```

### Scottish seats
#### 6. You can use COUNT and GROUP BY to see how each party did in Scotland. Scottish constituencies start with 'S'
#### Show how many seats for each party in Scotland in 2017.
```SQL
SELECT [ANSWER HERE] 
```