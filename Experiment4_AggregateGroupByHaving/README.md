# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- *MIN()* – Smallest value  
- *MAX()* – Largest value  
- *COUNT()* – Number of rows  
- *SUM()* – Total of values  
- *AVG()* – Average of values

*Syntax:*
sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;

### GROUP BY
Groups records with the same values in specified columns.
*Syntax:*
sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;

### HAVING
Filters the grouped records based on aggregate conditions.
*Syntax:*
sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;


*Question 1*

Write a SQL query to find the total amount of fruits with a unit type of 'LB'.
Note: Inventory attribute contains amount of fruits
Table: fruits

sql
SELECT
SUM(inventory) AS total
FROM fruits
WHERE unit LIKE '%LB%';


*Output:*

![image](https://github.com/user-attachments/assets/0116cf71-124c-45cb-a4fa-3e2921725b75)

*Question 2*

Write a SQL query to find how many employees have an income greater than 50K?
Table: employee

sql
SELECT
COUNT(*) AS employees_count
FROM employee
WHERE income>50000;


*Output:*

![image](https://github.com/user-attachments/assets/31ac50d2-9085-4ad7-868e-55ed26256912)

*Question 3*

Write a SQL query to find  how many employees work in California?
Table: employee

sql
SELECT
COUNT(*) AS employees_in_california
FROM employee
WHERE city='California';


*Output:*

![image](https://github.com/user-attachments/assets/79637ac1-4e65-4d11-8ed6-734109ed37b7)

*Question 4*

How many medical records does each doctor have?
Sample table:MedicalRecords Table

sql
SELECT
DoctorID,
COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY DoctorID
ORDER BY DoctorID ASC;


*Output:*

![image](https://github.com/user-attachments/assets/eae854bc-2a5d-40fc-aad0-a0786177bc99)

*Question 5*
What is the average duration of insurance coverage for patients covered by each insurance company?
Sample table:Insurance Table

sql
SELECT
InsuranceCompany,
ABS(AVG(StartDate-EndDate)) AS AvgCoverageDurationDays
FROM Insurance
GROUP BY InsuranceCompany;


*Output:*

![image](https://github.com/user-attachments/assets/cd4c7aeb-31ca-4bfd-9440-b5b16a7401a5)

*Question 6*

How many medical records are there for each patient?
Sample table:MedicalRecords Table

sql
SELECT
PatientID,
COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY PatientID
ORDER BY PatientID;


*Output:*

![image](https://github.com/user-attachments/assets/35c643a2-6a09-498d-ad86-06bd18cc9d7a)

*Question 7*

Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000.
Sample table: employee

sql
SELECT
age,
MIN(income) AS Income
FROM employee
GROUP BY age
HAVING MIN(income)<1000000;


*Output:*

![image](https://github.com/user-attachments/assets/e14f1a3b-6516-4fc9-83a3-4148ae6f22f6)

*Question 8*

Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the average work hours for each date, and excludes dates where the average work hour is not less than 10.
Sample table: employee1

sql
SELECT
jdate,
AVG(workhour) AS "AVG(workhour)"
FROM employee1
GROUP BY jdate
HAVING AVG(workhour)<10;


*Output:*

![image](https://github.com/user-attachments/assets/81e5fa74-f3ba-4255-9817-43c6514cc745)

*Question 9*

Write the SQL query that achieves the selection of product names and the maximum price for each category from the "products" table, and includes only those products where the maximum price is greater than 15.
Sample table: products

sql
SELECT
category_id,
product_name,
MAX(price) AS Price
FROM products
GROUP BY category_id 
HAVING MAX(price)>15;


*Output:*

![image](https://github.com/user-attachments/assets/08b6605d-fcb7-4aa0-898d-5ca912bcbdf4)

*Question 10*

Write the SQL query that accomplishes the selection of average price for each category from the "products" table and includes only those products where the average price falls between 10 and 15.
Sample table: products

sql
SELECT
category_id,
AVG(price) AS 'AVG(Price)'
FROM products
GROUP BY category_id
HAVING AVG(price) BETWEEN 10 AND 15;


*Output:*

![image](https://github.com/user-attachments/assets/cbae2ed5-e6eb-41b4-a4d2-aea7847693a7)

## Grade:

![Screenshot 2025-05-10 100902](https://github.com/user-attachments/assets/efe3fd54-d92e-4317-bfe8-ae6d9e58a32c)

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
