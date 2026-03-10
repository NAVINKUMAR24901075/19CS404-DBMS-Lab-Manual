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
```
Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees in employees table.

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
**Answer**
```
UPDATE employees
SET email='Unavailable'
```

**Output:**

<img width="1260" height="469" alt="image" src="https://github.com/user-attachments/assets/3279d15f-f9d6-4a73-94c2-28d696ed3ac4" />

**Question 2**
```
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

**Answer**

```
UPDATE Employees
SET salary=ROUND(salary*1.25)
WHERE department_id=40;

UPDATE Employees
SET salary=ROUND(salary*1.15)
WHERE department_id=90;

UPDATE Employees
SET salary=ROUND(salary*1.10)
WHERE department_id=110;

```

**Output:**

<img width="1710" height="373" alt="image" src="https://github.com/user-attachments/assets/ddb64e05-9873-4093-82b4-249bf8492cff" />


**Question 3**
```
Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```
**Answer**

```
UPDATE PRODUCTS
SET reorder_lvl=40
WHERE category='Grocery'
```

**Output:**

<img width="1889" height="344" alt="image" src="https://github.com/user-attachments/assets/4c4500d7-2409-41e5-a77b-4a6aa627afd0" />


**Question 4**
```
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

Suppliers Table 

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)

```
**Answer**

```
UPDATE Suppliers
SET address='58 Lakeview, Magnolia'
WHERE supplier_id=5
```

**Output:**

<img width="1854" height="323" alt="image" src="https://github.com/user-attachments/assets/9c71d3e9-2a63-4ad8-a65d-cd537491d35a" />


**Question 5**
```
For products with a profit % less than 30% of selling price, update the selling price to provide a profit margin of 35% over cost price of the product in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT
```
**Answer**

```
UPDATE PRODUCTS
SET sell_price = CAST(cost_price*1.35 AS INT)
WHERE ((sell_price-cost_price)/sell_price)*100<30;

```

**Output:**

<img width="1868" height="438" alt="image" src="https://github.com/user-attachments/assets/6ca867c5-8d05-439f-ab9a-994e6f9895ff" />


**Question 6**
```
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_country' must be 'India',

2. 'cus_city' must not be 'Chennai',

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
```
**Answer**

```
DELETE FROM Customer
WHERE cust_country='India'
AND cust_city!='Chennai';
```

**Output:**

<img width="1885" height="516" alt="image" src="https://github.com/user-attachments/assets/8ce2e0c1-7078-425d-a5b5-f00f6ff757ac" />


**Question 7**
```
Write a SQL query to delete a doctor from Doctors table whos specialization is 'Cardiology'

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
```
**Answer**

```
DELETE FROM Doctors
WHERE specialization='Cardiology'
```

**Output:**

<img width="1437" height="477" alt="image" src="https://github.com/user-attachments/assets/a28b60a0-a0f4-4973-ade1-b924c48bdd4a" />


**Question 8**
```
Write a SQL query to Delete All Doctors with a NULL Last Name

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
```
**Answer**

```
DELETE FROM Doctors
WHERE last_name IS NULL;
```

**Output:**

<img width="1478" height="768" alt="image" src="https://github.com/user-attachments/assets/e9bad206-421a-4414-8c97-860853dd7098" />


**Question 9**
```
Write a SQL query to Delete customers with 'GRADE' 2 and 'CUST_NAME' starting with 'M', and whose 'PAYMENT_AMT' is less than 3000

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
```
**Answer**

```
DELETE FROM Customer
WHERE GRADE=2
AND CUST_NAME LIKE 'M%'
AND PAYMENT_AMT<3000;
```

**Output:**

<img width="1872" height="239" alt="image" src="https://github.com/user-attachments/assets/6d998735-d563-4d5a-b85c-e58f995df407" />


**Question 10**
```
Write a SQL query to Delete a Specific Surgery which was made on 28th Feb 2024.

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date

```
**Answer**

```
DELETE FROM Surgeries
WHERE surgery_date = '2024-02-28'
```

**Output:**

<img width="1505" height="421" alt="image" src="https://github.com/user-attachments/assets/05297930-1b5c-4f65-9ba9-947e74cd65a7" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
