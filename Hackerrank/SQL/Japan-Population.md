# Japan Population

[문제 상세보기](https://www.hackerrank.com/challenges/japan-population/problem)

Query the sum of the populations for all Japanese cities in **CITY**. The *COUNTRYCODE* for Japan is **JPN**.

**Input Format**

The

**CITY**

table is described as follows:

![https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

## Flow.

- COUNTRYCODE 가 JPN인 도시의 총 인구합계를 구한다.

## SQL

```sql
SELECT sum(POPULATION) FROM CITY WHERE COUNTRYCODE='JPN'
```
