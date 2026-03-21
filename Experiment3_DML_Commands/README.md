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
## Question 1

Update the 'Selling_Price' to add 10% extra margin for all products supplied by the supplier with id 6.

PRODUCTS TABLE
```
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
```
UPDATE Products
SET sell_price=round(sell_price*1.10,0)
WHERE supplier_id=6;
```
## Output:

<img width="837" height="252" alt="image" src="https://github.com/user-attachments/assets/342d7a56-afab-4d40-826d-91f0e3590694" />


Question 2

Write a SQL statement to Update the reorder level to 20 where the quantity in stock is less than 10 and product category is 'Snacks' in the products table.

Products table

```
---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id
```
```
UPDATE Products
SET reorder_lvl=20
WHERE quantity<10 and category='Snacks';
```
Output:

<img width="844" height="278" alt="image" src="https://github.com/user-attachments/assets/72e9d54f-f8f8-4570-b356-c25eebf583d2" />


## Question 3

For Increase the selling price per unit by 3 for all products supplied by supplier ID 4 in the sales table.

PRODUCTS TABLE

```
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
SALES TABLE

```
name               type
-----------------  ---------------
sale_id            INT
sale_date          DATE
product_id         INT
quantity           INT
sell_price         DECIMAL(10,2)
total_sell_price   DECIMAL(10,2)
```
```
UPDATE SALES
SET sell_price=sell_price+3
WHERE product_id IN (SELECT product_id FROM PRODUCTS
WHERE supplier_id=4);
```

## Output:

<img width="842" height="174" alt="image" src="https://github.com/user-attachments/assets/3226d5fd-cd00-4b59-933f-b65cc380ab03" />

## Question 4

Write a SQL statement to double the availability of the product with product_id 1.

products table

```
---------------
product_id
product_name
category_id
availability
```
```
UPDATE products
SET availability=availability*2
WHERE product_id=1;
```
## Output:

<img width="806" height="144" alt="image" src="https://github.com/user-attachments/assets/b44a18d6-6c71-40d2-8de3-4f7f247cbb6a" />


## Question 5

Write a SQL statement to Increase quantity of all products by 10% to adjust for surplus stock counted

Products table

```
---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id
```
```
UPDATE Products
set quantity=(quantity*1.10);
```
## Output:

<img width="837" height="289" alt="image" src="https://github.com/user-attachments/assets/103d0068-b81d-4e95-9b44-1f9c9f10a6bf" />


## Question 6

Write a SQL query to Delete customers with 'GRADE' 3 or 'AGENT_CODE' 'A008' whose 'OUTSTANDING_AMT' is less than 5000

```
DELETE FROM Customer
WHERE (GRADE=3 OR AGENT_CODE='A008') AND OUTSTANDING_AMT < 5000;
```
Output:

<img width="841" height="176" alt="image" src="https://github.com/user-attachments/assets/894ca7ed-c2ce-432e-b01c-3a58f8d9967e" />


## Question 7

Write a SQL query to delete a specific doctor from Doctors table whose ID is 1.

Sample table: Doctors attributes : doctor_id, first_name, last_name, specialization

```
DELETE FROM Doctors
WHERE doctor_id=1;
```
## Output:

<img width="792" height="153" alt="image" src="https://github.com/user-attachments/assets/e4634b7a-a0ef-4d50-9703-fad9fed7ad71" />

Question 8

Write a SQL query to Delete customers whose 'GRADE' is greater than 2 and have a 'PAYMENT_AMT' less than the average 'PAYMENT_AMT' for all customers, or whose 'OUTSTANDING_AMT' is greater than 8000:

```
DELETE FROM Customer
WHERE (GRADE >2 AND PAYMENT_AMT < (SELECT AVG(PAYMENT_AMT) FROM Customer)) OR OUTSTANDING_AMT>8000;

```
## Output:

<img width="1106" height="254" alt="image" src="https://github.com/user-attachments/assets/772e4e55-8abe-4121-b638-4dcd9360da6c" />


## Question 9

Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.

```
DELETE FROM Customer
WHERE GRADE!=3;
```

## Output:

<img width="149" height="236" alt="image" src="https://github.com/user-attachments/assets/84fba900-c71c-4628-aa52-09286e656296" />


## Question 10

Write a SQL query to Delete All Doctors with a NULL Specialization

Sample table: Doctors attributes : doctor_id, first_name, last_name, specialization

```
DELETE FROM Doctors
WHERE specialization IS NULL;
```

## Output:

<img width="527" height="492" alt="image" src="https://github.com/user-attachments/assets/2baf5d80-8506-4503-8659-c55a5608f377" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
