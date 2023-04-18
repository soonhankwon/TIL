# Average Population of Each Continent

Given the **CITY** and **COUNTRY** tables, query the names of all the continents (*COUNTRY.Continent*) and their respective average city populations (*CITY.Population*) rounded *down* to the nearest integer.

**Note:** *CITY.CountryCode* and *COUNTRY.Code* are matching key columns.

**Input Format**

The **CITY** and **COUNTRY**

tables are described as follows:

![https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

![https://s3.amazonaws.com/hr-challenge-images/8342/1449769013-e54ce90480-Country.jpg](https://s3.amazonaws.com/hr-challenge-images/8342/1449769013-e54ce90480-Country.jpg)

## Flow.

- *CITY.CountryCode* and *COUNTRY.Code*
    - 두 테이블을 해당 컬럼으로 조인
- Group by COUNTRY.continent
    - 대륙으로 그룹화
- AVG 로 각 대륙 평균 도시 인구 & FLOOR 로 내림

## SQL.

```sql
SELECT COUNTRY.continent, FLOOR(AVG(CITY.population))
FROM CITY JOIN COUNTRY
ON CITY.countrycode = country.code
GROUP BY COUNTRY.continent
```
