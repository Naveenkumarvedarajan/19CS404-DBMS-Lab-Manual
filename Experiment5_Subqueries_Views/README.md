# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

*Types:*
- *Single-row subquery*:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- *Multiple-row subquery*:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- *Correlated subquery*:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

*Example:*
sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);

### Views
A view is a virtual table based on the result of an SQL SELECT query.
*Create View:*
sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;

*Drop View:*
sql
DROP VIEW view_name;


*Question 1*

![image](https://github.com/user-attachments/assets/d654bceb-bbff-42da-8721-00c5afae6ba8)

sql
SELECT 
medication_id AS medic,
medication_name,
dosage
FROM Medications
WHERE CAST(REPLACE(dosage,'mg','') AS INTEGER)=(SELECT MAX(CAST(REPLACE(dosage,'mg','') AS INTEGER))
FROM Medications);


*Output:*

![image](https://github.com/user-attachments/assets/a3e71cc8-f0c6-4faf-bace-2fbfb6737fb3)

*Question 2*

![image](https://github.com/user-attachments/assets/ccb89df8-b38a-4233-9ace-d6d304460b7e)

sql
SELECT
o.ord_no,
o.purch_amt,
o.ord_date,
o.customer_id,
o.salesman_id
FROM Orders o
JOIN Salesman s ON o.salesman_id=s.salesman_id
WHERE s.city='New York';


*Output:*

![image](https://github.com/user-attachments/assets/81124a54-70e1-4c49-be59-149c9204e74b)

*Question 3*

![image](https://github.com/user-attachments/assets/6431ed32-fca6-4b48-ab95-0ddc3374a142)

sql
SELECT student_name,grade
FROM GRADES
WHERE grade IN(SELECT MIN(grade) FROM GRADES AS g WHERE g.subject=GRADES.subject);


*Output:*

![image](https://github.com/user-attachments/assets/748c9d89-a4d2-49f8-9680-30e9df543c4a)

*Question 4*

![image](https://github.com/user-attachments/assets/10efed41-7e0b-41e4-906f-64bcedf421f8)

sql
SELECT *
FROM customer
WHERE city <>(
SELECT
city
FROM customer
WHERE id=(SELECT MAX(id) FROM customer));


*Output:*

![image](https://github.com/user-attachments/assets/9daeadc7-5869-4b93-86f3-8a5b73ed92ae)

*Question 5*

![image](https://github.com/user-attachments/assets/eda18ec5-88a9-4c7e-90ab-41b36996da57)

sql
SELECT 
name
FROM customer
WHERE phone IN(
SELECT phone
FROM customer
GROUP BY phone
HAVING COUNT(*)=1)


*Output:*

![image](https://github.com/user-attachments/assets/3b98e683-d591-4361-9d2b-ddd1e986e384)

*Question 6*

![image](https://github.com/user-attachments/assets/b7bed10d-a021-486e-8c02-d44cb88bfe6c)

sql
SELECT *
FROM GRADES
WHERE grade IN(SELECT MAX(grade) FROM GRADES AS g WHERE g.subject=GRADES.subject);


*Output:*

![image](https://github.com/user-attachments/assets/f4ce0e26-e799-4a9b-8457-5126245dc9c7)

*Question 7*

![image](https://github.com/user-attachments/assets/ccbb6475-2aac-4bff-8ba8-92ef9fe8f53c)

sql
SELECT
o.ord_no,
o.purch_amt,
o.ord_date,
o.customer_id,
o.salesman_id
FROM Orders o
JOIN Salesman s ON o.salesman_id=s.salesman_id
WHERE s.city='New York';


*Output:*

![image](https://github.com/user-attachments/assets/57cfdde4-e475-4666-9677-1fd8d10b2022)

*Question 8*

![image](https://github.com/user-attachments/assets/9e787c14-9fc4-49a2-b3c1-cd4c69485cb8)

sql
SELECT *
FROM GRADES
WHERE grade IN(SELECT MIN(grade) FROM GRADES AS g WHERE g.subject=GRADES.subject);


*Output:*

![image](https://github.com/user-attachments/assets/ce5feb2b-9dfc-4980-9411-5edcf3702d42)

*Question 9*

![image](https://github.com/user-attachments/assets/2a05d48d-022b-4e97-a201-05713a268e27)

sql
SELECT * 
FROM Orders
WHERE salesman_id IN(
SELECT
salesman_id
FROM Orders
WHERE customer_id='3007');


*Output:*

![image](https://github.com/user-attachments/assets/9ff96a98-0982-40ff-80b5-3aaf683b7291)

*Question 10*

![image](https://github.com/user-attachments/assets/cc29af2d-603e-42d1-8253-27e7f9d87c5b)

sql
SELECT *
FROM Employee
WHERE age<(SELECT AVG(age) FROM Employee WHERE income>250000);


*Output:*

![image](https://github.com/user-attachments/assets/8c1a1b55-6e6e-4b5f-a0ed-98f6e47e7730)

## Grade:
![image](https://github.com/user-attachments/assets/2a6e7a99-4862-48ed-917a-ed11be2bf25e)


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
