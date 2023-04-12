# Average Polulation
Query the average population for all cities in **CITY**, rounded *down* to the nearest integer.

**Input Format**

The

**CITY**

table is described as follows:

![https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

## Flow.

- rounded down : truncate(숫자, 0)
    - 숫자를 버릴 자릿수 아래로 버림
- average : avg()

## SQL.

```sql
SELECT truncate(avg(POPULATION),0) FROM CITY
```
