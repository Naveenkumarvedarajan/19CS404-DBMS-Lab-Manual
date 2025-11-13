# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

*Syntax:*
sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;


### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

*Syntax:*

sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;

### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

*Syntax:*

sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;

### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

*Syntax:*

sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;


*Question 1*

![image](https://github.com/user-attachments/assets/673d6702-5c57-4e90-a19d-7787fea13ea1)

sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.city AS "city",
    s.commission
FROM 
    customer c
JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    c.city <> s.city
    AND s.commission > 0.12;


*Output:*

![image](https://github.com/user-attachments/assets/40c70ce9-e9c2-409c-9073-e9d80675e9d9)

*Question 2*

![image](https://github.com/user-attachments/assets/f993bb08-2c69-4f9f-afcc-43b31212292f)

sql
SELECT DISTINCT c.cust_name
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id AND o.purch_amt < 100
WHERE o.purch_amt IS NOT NULL;


*Output:*

![image](https://github.com/user-attachments/assets/fb36ee01-8c41-4360-9d75-d77798fcbc60)

*Question 3*

![image](https://github.com/user-attachments/assets/ee5b4049-bdd5-44fe-ac21-89877b009d52)

sql
SELECT 
    s.name AS Salesman,
    c.cust_name,
    s.city
FROM 
    salesman AS s
INNER JOIN 
    customer AS c
ON 
    s.city = c.city;


*Output:*

![image](https://github.com/user-attachments/assets/28c5d386-5ae6-4c1c-9f2d-1e70c95ddd1c)

*Question 4*

![image](https://github.com/user-attachments/assets/b104a123-5814-4dbe-bd04-bf9a432f3c23)

sql
SELECT 
    s.name
FROM 
    salesman AS s
LEFT JOIN 
    customer AS c
ON 
    s.salesman_id = c.salesman_id
WHERE 
    c.city = 'London';


*Output:*

![image](https://github.com/user-attachments/assets/44918bad-2f3f-462b-80c4-2ae9bbebc4a6)

*Question 5*

![image](https://github.com/user-attachments/assets/589e3b80-3e86-48a4-879a-e9a617b894d1)

sql
SELECT 
    p.first_name AS patient_name, 
    d.first_name AS doctor_name
FROM 
    patients AS p
INNER JOIN 
    doctors AS d
ON 
    p.doctor_id = d.doctor_id
WHERE 
    p.date_of_birth > '1990-01-01';


*Output:*

![image](https://github.com/user-attachments/assets/896be61c-a9bd-4c78-be22-0de19923b737)

*Question 6*

![image](https://github.com/user-attachments/assets/29dda45f-7000-4d82-9a48-f7d92a581816)

sql
SELECT 
    c.cust_name, 
    o.ord_no, 
    o.ord_date, 
    o.purch_amt
FROM 
    customer AS c
LEFT JOIN 
    orders AS o
ON 
    c.customer_id = o.customer_id
WHERE 
    o.purch_amt > 1000;


*Output:*

![image](https://github.com/user-attachments/assets/c3358f55-b082-402f-8797-a31f1e43eda1)

*Question 7*

![image](https://github.com/user-attachments/assets/436efb4f-58ab-4346-9e64-11378c1988a3)

sql
SELECT 
    c.*
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
WHERE 
    o.ord_date > '2012-08-17';


*Output:*

![image](https://github.com/user-attachments/assets/e84815a8-57e5-48cc-9077-500ad4def0a2)

*Question 8*

![image](https://github.com/user-attachments/assets/874af454-bc6f-4b65-9b71-47e5e2afa5de)

sql
SELECT 
    p.date_of_birth, 
    a.*
FROM 
    patients AS p
INNER JOIN 
    appointments AS a
ON 
    p.patient_id = a.patient_id
WHERE 
    p.first_name = 'Alice';


*Output:*

![image](https://github.com/user-attachments/assets/b9bc1227-56a9-4bbd-a820-f3d58e0efec2)

*Question 9*

![image](https://github.com/user-attachments/assets/bcf67c0e-23e8-49e6-bc98-0db86d741c6b)

sql
SELECT p.*
FROM patients p
INNER JOIN test_results t ON p.patient_id = t.patient_id
WHERE t.test_name = 'X-Ray' AND t.result = 'Normal';


*Output:*

![image](https://github.com/user-attachments/assets/d5b063f6-d7ea-4b48-895d-bbdc4f3c61bf)

*Question 10*

![image](https://github.com/user-attachments/assets/9a24c7e1-2d5d-4993-98cd-6ab3c9dfec67)

sql
SELECT 
    patients.first_name AS patient_name,
    doctors.first_name AS doctor_name
FROM 
    patients
INNER JOIN 
    doctors ON patients.doctor_id = doctors.doctor_id
WHERE 
    patients.discharge_date IS NULL;


*Output:*

![image](https://github.com/user-attachments/assets/70ec372d-8e59-4771-ad40-7c5d8c7a0e8b)

## Grade:
![image](https://github.com/user-attachments/assets/96292f18-12e7-45dc-843a-a772c904096f)

## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
