# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
Write a SQL query to determine the age group of value1 in the Calculations table as 'Child' if it is less than 13, 'Teen' if it is between 13 and 19, and 'Adult' if it is 20 or older.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0

```
SELECT id,value1,
CASE
WHEN value1 < 13 THEN 'Child'
WHEN value1 BETWEEN 13 AND 19
THEN 'Teen'
ELSE 'Adult'
END AS age_group
FROM Calculations;

```


**Output:**


<img width="1128" height="472" alt="image" src="https://github.com/user-attachments/assets/a3675d32-a17f-47b3-b75b-4dc82721e14a" />


**Question 2**

Write a SQL query to retrieve the year, month, and day from the hiredate column in the emp table.

```
SELECT
strftime('%Y',hiredate) AS Year,
strftime('%m',hiredate) AS Month,
strftime('%d',hiredate) AS Day
FROM emp;
```

**Output:**

<img width="1218" height="480" alt="image" src="https://github.com/user-attachments/assets/ab513051-8168-48d3-b824-51815713d428" />


**Question 3**
---
Write a SQL query to Select all patients who were admitted for one day.

Table: Patients

name                  type
--------------------  ----------
patient_id            INT
first_name            VARCHAR(50)
last_name             VARCHAR(50)
date_of_birth         DATE
admission_date        DATE
discharge_date        DATE
doctor_id             INT

```
SELECT patient_id,first_name,
admission_date, discharge_date
FROM Patients
WHERE admission_date = 
discharge_date;

```

**Output:**

<img width="1162" height="451" alt="image" src="https://github.com/user-attachments/assets/5ab6eaf3-cd1c-4dd4-b43d-2c59acdf95fc" />


**Question 4**
---
Write a SQL query to calculate the absolute value of the value1 column from the Calculations table.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0

```
SELECT id,value1,ABS(value1) AS
absolute_value
FROM Calculations;
```
 

**Output:**

<img width="1198" height="417" alt="image" src="https://github.com/user-attachments/assets/f410e643-2c6b-48a7-9c7d-2bbe0a35d431" />


**Question 5**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' contains the substring 'Holmes'.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000

```
DELETE from customer
where CUST_NAME LIKE '%Holmes%';
```

**Output:**

<img width="1221" height="670" alt="image" src="https://github.com/user-attachments/assets/27da209e-b914-45fa-afca-aeba35b1eb49" />


**Question 6**
---
Write a SQL statement to Find the salesmen with all information who gets the commission within a range of 0.12 and 0.14.

salesman table

cid         name         type        notnull     dflt_value  pk
----------  -----------  ----------  ----------  ----------  ----------
0           salesman_id  numeric(5)    0                       1
1           name         varchar(30)   0                       0
2           city         varchar(15)   0                       0
3           commission   decimal(5,2)  0                       0

```
select *
from salesman
where commission  BETWEEN 0.12 AND 0.14;
```


**Output:**

<img width="1203" height="595" alt="image" src="https://github.com/user-attachments/assets/cd2f0e8d-b9f3-46e2-bacd-73ed55b7a315" />


**Question 7**
---
Write a SQL query to delete a doctor from Doctors table whose Specialization is 'Pediatrics' and First name is 'Michael'.

Sample table: Doctors

attributes: doctor_id, first_name, last_name, specialization

```
delete from Doctors
where specialization = 'Pediatrics'
AND first_name = 'Michael'
```

**Output:**

<img width="1176" height="489" alt="image" src="https://github.com/user-attachments/assets/e35ef1f9-8636-4a29-bc6b-5504372b5e88" />


**Question 8**
---
Write a SQL statement to increase the salary of employees under the department 40, 90 and 110 according to the company rules.

Salary will be increased by 25% for the department 40, 15% for department 90 and 10% for the department 110 and the rest of the departments will remain same.


Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id 

```
update Employees
set salary = case
when department_id = 40 then
cast (round (salary * 1.25) as integer)
when department_id = 90 then
cast (round(salary * 1.15) as integer) 
when department_id = 110 then
cast (round(salary * 1.10) as integer) 
else salary
end;
```

**Output:**

<img width="1201" height="571" alt="image" src="https://github.com/user-attachments/assets/1e2df904-7f37-4452-b641-cd1e5b921fbd" />


**Question 9**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is exactly 2.

 
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |        6000.00 |BBBBSBB  | A008       |
```
delete from customer
where GRADE = 2;
```



**Output:**

<img width="536" height="338" alt="image" src="https://github.com/user-attachments/assets/e04ab700-a711-4f8a-8559-7a5bf72378c2" />


**Question 10**
---
Write a SQL statement to double the availability of the product with product_id 1.


products table

---------------
product_id
product_name
category_id
availability 

```
update products
set availability = availability * 2
where product_id = 1;
```

**Output:**

<img width="1195" height="366" alt="image" src="https://github.com/user-attachments/assets/75dbd0c6-3e45-4cc6-b4fe-bb4f1134f049" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
