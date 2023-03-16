Write a query that prints a list of employee names (i.e.: the *name* attribute) from the **Employee** table in alphabetical order.

**Input Format**

The **Employee** table containing employee data for a company is described as follows:

![https://s3.amazonaws.com/hr-challenge-images/19629/1458557872-4396838885-ScreenShot2016-03-21at4.27.13PM.png](https://s3.amazonaws.com/hr-challenge-images/19629/1458557872-4396838885-ScreenShot2016-03-21at4.27.13PM.png)

where *employee_id* is an employee's ID number, *name* is their name, *months* is the total number of months they've been working for the company, and *salary* is their monthly salary.

**Sample Input**

![https://s3.amazonaws.com/hr-challenge-images/19629/1458558202-9a8721e44b-ScreenShot2016-03-21at4.32.59PM.png](https://s3.amazonaws.com/hr-challenge-images/19629/1458558202-9a8721e44b-ScreenShot2016-03-21at4.32.59PM.png)

**Sample Output**

```
Angela
Bonnie
Frank
Joe
Kimberly
Lisa
Michael
Patrick
Rose
Todd
```

### SQL

```sql
SELECT name FROM EMPLOYEE 
ORDER BY name;
```

### Summary.

- a list of employee names from the **Employee** table
    - SELECT name From EMPLOYEE
- in alphabetical order
    - ORDER BY name
