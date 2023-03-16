# Type of Triangle
Write a query identifying the *type* of each record in the **TRIANGLES** table using its three side lengths. Output one of the following statements for each record in the table:

- **Equilateral**: It's a triangle with 3 sides of equal length.
- **Isosceles**: It's a triangle with 2 sides of equal length.
- **Scalene**: It's a triangle with 3 sides of differing lengths.
- **Not A Triangle**: The given values of *A*, *B*, and *C* don't form a triangle.

**Input Format**

The **TRIANGLES** table is described as follows:

![https://s3.amazonaws.com/hr-challenge-images/12887/1443815629-ac2a843fb7-1.png](https://s3.amazonaws.com/hr-challenge-images/12887/1443815629-ac2a843fb7-1.png)

Each row in the table denotes the lengths of each of a triangle's three sides.

**Sample Input**

![https://s3.amazonaws.com/hr-challenge-images/12887/1443815827-cbfc1ca12b-2.png](https://s3.amazonaws.com/hr-challenge-images/12887/1443815827-cbfc1ca12b-2.png)

**Sample Output**

`Isosceles
Equilateral
Scalene
Not A Triangle`

### SQL

```sql
SELECT CASE 
WHEN A + B <= C OR A + C <= B OR B + C <= A THEN 'Not A Triangle' 
WHEN A = B AND B = C THEN 'Equilateral' 
WHEN A = B OR B = C OR A = C THEN 'Isosceles' 
ELSE 'Scalene' 
END AS triangle_type
FROM TRIANGLES;
```

### Summary

- identifying the *type* of each record in the **TRIANGLES** table using its three side lengths
    - SELECT CASE WHEN {Condition} THEN {result}
    - Equilateral(정삼각형)
    - Isosceles(이등변 삼각형)
    - Scalene(부등변 삼각형)
- **END AS** triangle_type
    - CASE 문 블록이 끝나고 출력 열(column) 이름을 정의
