# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.

```
create table Products(
       ProductID  INTEGER primary key,
       ProductName  TEXT  unique  not NULL,
       Price  REAL CHECK (Price > 0),
       StockQuantity  INTEGER CHECK (StockQuantity >= 0)

);
```

**Output:**

<img width="595" height="194" alt="image" src="https://github.com/user-attachments/assets/6e70daab-3ead-41dd-aa45-2e0ef4e58af5" />



**Question 2**
---
Create a table named Departments with the following columns:

DepartmentID as INTEGER
DepartmentName as TEXT

```
create table Departments(
       DepartmentID  INTEGER,
       DepartmentName  TEXT 



);
```

**Output:**


<img width="603" height="229" alt="image" src="https://github.com/user-attachments/assets/782c6aeb-b774-451a-bebc-d45eacc29079" />


**Question 3**
---
Write a SQL query to Rename the "city" column to "location" in the "customer" table.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002



```
Alter table customer
Rename column city to location;
```

**Output:**

<img width="1215" height="456" alt="image" src="https://github.com/user-attachments/assets/9c4401b5-1486-44f8-9b32-cc974efd45e9" />


**Question 4**


Create a table named Customers with the following columns:

CustomerID as INTEGER
Name as TEXT
Email as TEXT
JoinDate as DATETIME

```
create table customers(
       CustomerID  INTEGER,
       Name  TEXT,
       Email  TEXT,
       JoinDate DATETIME 



);
```

**Output:**

<img width="601" height="273" alt="image" src="https://github.com/user-attachments/assets/fd8ade76-f1be-4491-9730-89a10372c17c" />


**Question 5**
---

Insert the below data into the Books table, allowing the Publisher and Year columns to take their default values.

ISBN             Title                 Author
---------------  --------------------  ---------------
978-6655443321   Big Data Analytics    Karen Adams

Note: The Publisher and Year columns will use their default values.

```
insert into Books(ISBN,Title,Author)
values('978-6655443321','Big Data Analytics','Karen Adams');
```

**Output:**

<img width="1209" height="436" alt="image" src="https://github.com/user-attachments/assets/3c54ed9b-b330-4a61-bb1f-b26ca83367be" />

**Question 6**
---
Create a table named Tasks with the following columns:

TaskID as INTEGER
TaskName as TEXT
DueDate as DATE

```
create table Tasks(
       TaskID INTEGER,
       TaskName  TEXT,
       DueDate  DATE 

);
```

**Output:**

<img width="1180" height="472" alt="image" src="https://github.com/user-attachments/assets/8206d6ce-ed0c-4106-8df4-fcc975621c36" />


**Question 7**
---

Insert the below data into the Customers table, allowing the City and ZipCode columns to take their default values.

CustomerID  Name          Address
----------  ------------  ----------
304         Peter Parker  Spider St      

Note: The City and ZipCode columns will use their default values.

 ```
insert into Customers(CustomerID, Name, Address) 
values(304,'Peter Parker','Spider St');
```

**Output:**

<img width="1180" height="441" alt="image" src="https://github.com/user-attachments/assets/376eeef2-df80-48b3-b939-bb45f274fa30" />


**Question 8**
---
Write an SQL Query to add the attributes designation, net_salary, and dob to the Companies table with the following data types:
designation as VARCHAR(50)
net_salary as NUMBER
dob as DATE
```
Alter table Companies
add column designation  varchar(50); 
Alter table Companies
add column net_salary  number; 
Alter table Companies
add column  dob  date;
```


**Output:**

<img width="602" height="259" alt="image" src="https://github.com/user-attachments/assets/46444ee3-0a55-4fcd-b38d-0bd6c0c42f96" />


**Question 9**
---
Write a SQL Query for inserting the below values in the table Customers

ID               NAME             AGE  ADDRESS     SALARY      
---------------  ---------------  ---  ----------  ----------  
1                Ramesh           32   Ahmedabad   2000
2                Khilan           25   Delhi       1500
3                Kaushik          23   Kota        2000

```
insert into Customers values(1,'Ramesh',32,'Ahmedabad',2000);
insert into Customers values(2,'Khilan',25,'Delhi',1500);
insert into Customers values(3,'Kaushik',23,'Kota',2000);
```

**Output:**

<img width="602" height="197" alt="image" src="https://github.com/user-attachments/assets/1492d77e-792f-40f8-be31-8e4bd2a34249" />


**Question 10**
---
Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.
```

create table Department(
       DepartmentID integer primary key,
       DepartmentName text unique not null,
       Location text
);
```

**Output:**

<img width="608" height="206" alt="image" src="https://github.com/user-attachments/assets/2177a18e-a851-4f2f-a92e-fbf168868df8" />


RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
