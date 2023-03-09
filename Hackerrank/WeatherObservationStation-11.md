# **Weather Observation Station 11**

Query the list of *CITY* names from **STATION** that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.

**Input Format**

The **STATION** table is described as follows:

![https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

where *LAT_N* is the northern latitude and *LONG_W* is the western longitude.

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE 
CITY REGEXP '^[^aeiou]' OR CITY REGEXP '[^aeiou]$'
```

## Summary.

- SELECT DISTINCT CITY FROM STATION
    - the list of *CITY* names from **STATION**
- do not start with vowels or do not end with vowels
    - WHERE CITY REGEXP '^[^aeiou]' OR CITY REGEXP '[^aeiou]$'
- REGEXP (Regular Expression)
    - ^ : 문자열의 시작
    - [^aeiou] : 모음을 제외한 문자
    - $ : 문자열의 끝
    - ex) REGEXP '[a-z][^aeiou]$' 모음으로 끝나지 않는 모든 CITY
