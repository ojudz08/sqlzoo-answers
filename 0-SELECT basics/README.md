### SELECT basics
| name | continet | area | population | gdp |
| :--- | :--- | :--- | :--- | :--- |
| Afghanistan | Asia | 652230 | 25500100 | 20343000000 |
| Albania | Asia |  |  |  |
| Algeria | Africa |  |  |  |
| Andorra | Europe |  |  |  |
| Angola | Africa |  |  |  |

## Answers
Introducing the world table countries

1. Show the population of Germany
```SQL
SELECT population FROM world
  WHERE name = 'Germany'
```