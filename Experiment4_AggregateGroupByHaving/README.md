# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

## Question 1

How many appointments are scheduled for each doctor?

```
SELECT DoctorID, COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DoctorID
ORDER BY DoctorID;
```
## Output:

<img width="711" height="614" alt="image" src="https://github.com/user-attachments/assets/8bf1ede4-34f7-4c83-aed8-cd62e78d9db1" />


## Question 2

What is the average dosage prescribed for each medication?

```
SELECT Medication,AVG(Dosage) AS AvgDosage
FROM Prescriptions
GROUP BY Medication
ORDER BY Medication;
```

## Output:

<img width="607" height="717" alt="image" src="https://github.com/user-attachments/assets/854ea325-e7d6-4321-a5f0-160390b5abd4" />


## Question 3

How many patients are there in each city?

```
SELECT Address,COUNT(*) AS TotalPatients
FROM Patients
GROUP BY Address
ORDER BY Address;
```

## Output:

<img width="611" height="387" alt="image" src="https://github.com/user-attachments/assets/ebed9361-c96e-422c-9ff2-ee57a757e427" />


## Question 4

Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.

```
SELECT COUNT(*) AS COUNT FROM customer
WHERE city!='Noida';
```

## Output:

<img width="321" height="266" alt="image" src="https://github.com/user-attachments/assets/c6f2aeca-9527-4a41-8b30-91785c0313d1" />


## Question 5

Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.

Sample table: orders

ord_no purch_amt ord_date customer_id salesman_id


70001 150.5 2012-10-05 3005 5002

70009 270.65 2012-09-10 3001 5005

70002 65.26 2012-10-05 3002 5001

```
SELECT AVG(purch_amt) AS AVERAGE
FROM orders;
```

## Output:

<img width="338" height="298" alt="image" src="https://github.com/user-attachments/assets/5564a094-169d-4f0f-9509-bacba898fde7" />


## Question 6

Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer

customer_id | cust_name | city | grade | salesman_id

-------------+----------------+------------+-------+-------------

```

    3002 | Nick Rimando   | New York   |   100 |        5001

    3007 | Brad Davis     | New York   |   200 |        5001

    3005 | Graham Zusi    | California |   200 |        5002
```
```
SELECT COUNT(*) AS COUNT FROM customer
WHERE grade IS NOT NULL;
```

## Output:

<img width="329" height="286" alt="image" src="https://github.com/user-attachments/assets/0bb08a3e-e379-45c9-a0ab-da3d3d929032" />


## Question 7

Write a SQL query to find how many employees have an income greater than 50K?

Table: employee

name type

id INTEGER name TEXT age INTEGER city TEXT income INTEGER

```
SELECT COUNT(*) AS employees_count FROM employee
WHERE income>50000;
```

## Output:

<img width="413" height="296" alt="image" src="https://github.com/user-attachments/assets/fd9c603c-54e1-4bc5-91e4-582670e0774a" />


## Question 8

Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the total salary sum for each group, and excludes groups where the total salary sum is not greater than 5000.

```
SELECT (age/5)*5 AS age_group,SUM(salary)
FROM customer1
GROUP BY age_group
HAVING SUM(salary)>5000;
```
## Output:

<img width="580" height="333" alt="image" src="https://github.com/user-attachments/assets/7981eea9-9907-42ea-bb93-ffc323c3b53d" />


## Question 9

Write the SQL query that achieves the grouping of data by city, calculates the average income for each city, and includes only those cities where the average income is greater than 500,000.

```
SELECT city,AVG(income)
FROM employee
GROUP BY city
HAVING AVG(income)>500000;
```

## Output:

<img width="575" height="406" alt="image" src="https://github.com/user-attachments/assets/012d45a7-ace8-4461-bae0-6c381821fb80" />


## Question 10

Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

```
SELECT occupation,AVG(workhour)
FROM employee1
GROUP BY occupation
HAVING AVG(workhour) BETWEEN 10 AND 12;
```

## Output:


<img width="623" height="365" alt="image" src="https://github.com/user-attachments/assets/c08f5640-4ae5-4b02-b548-8955960b578b" />


