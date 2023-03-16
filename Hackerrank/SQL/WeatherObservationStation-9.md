# **Weather Observation Station 9**

Query the list of *CITY* names from **STATION** that *do not start* with vowels. Your result cannot contain duplicates.

**Input Format**

The **STATION** table is described as follows:

![table](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

```sql
SELECT DISTINCT CITY FROM STATION
WHERE CITY NOT LIKE 'A%' 
AND CITY NOT LIKE 'E%' 
AND CITY NOT LIKE 'I%' 
AND CITY NOT LIKE 'O%' 
AND CITY NOT LIKE 'U%';
```
### Summary

- DISTICT : 중복제거
- Vowel은 모음이다 (A,E,I,O,U)
- do not start with vowels
- NOT LIKE 'A%' : A로 시작하지 않는 CITY들
- LIKE 'A%' : A로 시작하는 CITY들 
