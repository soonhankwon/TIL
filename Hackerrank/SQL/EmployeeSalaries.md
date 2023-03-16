# Employee Salaries
Write a query that prints a list of employee names (i.e.: the *name* attribute) for employees in **Employee** having a salary greater than  per month who have been employees for less than  months. Sort your result by ascending *employee_id*.

**Input Format**

The **Employee** table containing employee data for a company is described as follows:

![https://s3.amazonaws.com/hr-challenge-images/19629/1458557872-4396838885-ScreenShot2016-03-21at4.27.13PM.png](https://s3.amazonaws.com/hr-challenge-images/19629/1458557872-4396838885-ScreenShot2016-03-21at4.27.13PM.png)

where *employee_id* is an employee's ID number, *name* is their name, *months* is the total number of months they've been working for the company, and *salary* is the their monthly salary.

**Sample Input**

![https://s3.amazonaws.com/hr-challenge-images/19630/1458558612-af3da3ceb7-ScreenShot2016-03-21at4.32.59PM.png](https://s3.amazonaws.com/hr-challenge-images/19630/1458558612-af3da3ceb7-ScreenShot2016-03-21at4.32.59PM.png)

**Sample Output**

`Angela
Michael
Todd
Joe`

**Explanation**

*Angela* has been an employee for $3443 month and earns  per month.

*Michael* has been an employee for $2017 months and earns  per month.

*Todd* has been an employee for $3396 months and earns  per month.

*Joe* has been an employee for $3573 months and earns  per month.

We order our output by ascending *employee_id*.

### SQL.

```sql
SELECT name FROM Employee
WHERE salary > 2000 AND months < 10
ORDER BY employee_id ASC;
```

### Summary.

- a list of employee names from Employee table
    - SELECT name FROM Employee
- having a salary greater than per month who have been employees for less than 10 months.
    - WHERE salary > 2000 AND months < 10;
- Sort your result by ascending *employee_id*
    - ORDER BY employee_id ASC
