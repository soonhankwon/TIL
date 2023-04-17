# Population Density Difference
Query the difference between the maximum and minimum populations in **CITY**.

**Input Format**
The **CITY** table is described as follows:

![https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

## SQL

```sql
SELECT max(population) - min(population) 
FROM CITY
```
