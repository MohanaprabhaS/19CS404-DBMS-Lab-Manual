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
Insert a book with ISBN 978-1234567890, Title Data Science Essentials, Author Jane Doe, Publisher TechBooks, and Year 2024 into the Books table.

## Code:
```
INSERT INTO Books(ISBN,Title,Author,Publisher,Year)
VALUES("978-1234567890","Data Science Essentials","Jane Doe","TechBooks",2024);
```
**Output:**

<img width="838" height="124" alt="image" src="https://github.com/user-attachments/assets/a658c6fc-d99f-4bf3-8959-b615bcb5dffe" />


**Question 2**
Insert all customers from Old_customers into Customers

Table attributes are CustomerID, Name, Address, Email

## Code:
```
INSERT INTO Customers
VALUES('301',"Michael Johnson","123 Elm Street","michael.j@example.com");


INSERT INTO Customers
VALUES('302',"Sarah Lee","456 Oak Avenue","sarah.lee@example.com");


INSERT INTO Customers
VALUES('303',"David Wilson","789 Pine Road","david.w@example.com");
```

**Output:**

<img width="841" height="120" alt="image" src="https://github.com/user-attachments/assets/a816d187-6a93-47fd-a8af-89504cc6f723" />


**Question 3**
Create a table named ProjectAssignments with the following constraints: AssignmentID as INTEGER should be the primary key. EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID). ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID). AssignmentDate as DATE should be NOT NULL.

## Code:
```
CREATE TABLE ProjectAssignments
(
AssignmentID INTEGER primary key,
EmployeeID INTEGER,
ProjectID INTEGER,
AssignmentDate DATE NOT NULL,
foreign key (EmployeeID) references Employees(EmployeeID),
foreign key (ProjectID) references Projects(ProjectID)
);
```
**Output:**

<img width="817" height="174" alt="image" src="https://github.com/user-attachments/assets/823081e6-25a3-4eed-83ca-5d5c650dfd4c" />


**Question 4**
Create a table named Products with the following constraints: ProductID as INTEGER should be the primary key. ProductName as TEXT should be unique and not NULL. Price as REAL should be greater than 0. StockQuantity as INTEGER should be non-negative.

## Code:
```
CREATE TABLE Products
(
ProductID INTEGER primary key,
ProductName TEXT UNIQUE NOT NULL,
Price REAL CHECK(Price>0),
StockQuantity INTEGER CHECK(StockQuantity>0)
);
```

**Output:**

<img width="826" height="195" alt="image" src="https://github.com/user-attachments/assets/6867a4fa-a6b8-4d9d-bc06-9ae284f51de5" />


**Question 5**
Write a SQL query to modify the Student_details table by adding a new column Email of type VARCHAR(50) and updating the column MARKS to have a default value of 0.

## Code:
```
ALTER TABLE Student_details
ADD COLUMN Email VARCHAR(50);

ALTER TABLE Student_details
ADD COLUMN MARKS INTEGER DEFAULT 0;
```

**Output:**

<img width="838" height="95" alt="image" src="https://github.com/user-attachments/assets/4612ade6-b119-483d-8d74-93b7f990a9bd" />

**Question 6**
Write a SQL query to Rename the "city" column to "location" in the "customer" table.

## Code:
```
ALTER TABLE customer
RENAME COLUMN city to location;
```
## Output:

<img width="842" height="142" alt="image" src="https://github.com/user-attachments/assets/e6507e39-1e76-4c1a-b739-9574237b3a11" />


**Question 7**
Insert the following students into the Student_details table: RollNo Name Gender Subject MARKS

202 Ella King F Chemistry 87 203 James Bond M Literature 78

## Code:
```
INSERT INTO Student_details
VALUES(202,"Ella King","F","Chemistry",87);


INSERT INTO Student_details
VALUES(203,"James Bond","M","Literature",78);
```
## Output:

<img width="770" height="129" alt="image" src="https://github.com/user-attachments/assets/97e039ac-1dcc-4f73-a2b7-c381116eec38" />


**Question 8**
Create a new table named item with the following specifications and constraints: item_id as TEXT and as primary key. item_desc as TEXT. rate as INTEGER. icom_id as TEXT with a length of 4. icom_id is a foreign key referencing com_id in the company table. The foreign key should cascade updates and deletes. item_desc and rate should not accept NULL.

## Code:
```
CREATE TABLE item
(
item_id TEXT primary key,
item_desc TEXT NOT NULL,
rate INTEGER NOT NULL,
icom_id TEXT(4),
foreign key (icom_id) references company(com_id) ON UPDATE CASCADE ON DELETE CASCADE
);
```

## Output:

<img width="654" height="186" alt="image" src="https://github.com/user-attachments/assets/eec30924-c27d-4ecd-915a-cba53e28f509" />


**Question 9**
Create a table named Orders with the following columns:

OrderID as INTEGER OrderDate as TEXT CustomerID as INTEGER

## Code:
```
CREATE TABLE Orders
(
OrderID INTEGER,
OrderDate TEXT,
CustomerID INTEGER
);
```

## Output:

<img width="837" height="215" alt="image" src="https://github.com/user-attachments/assets/2673504b-584d-422f-83ba-63f844d58c28" />


**Question 10**
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key. InvoiceDate as DATE. DueDate as DATE should be greater than the InvoiceDate. Amount as REAL should be greater than 0.

## Code:
```
CREATE TABLE Invoices
(
InvoiceID INTEGER primary key,
InvoiceDate DATE,
DueDate DATE CHECK(DueDate>InvoiceDate),
Amount REAL CHECK(Amount>0)
);
```
## Output:

<img width="677" height="130" alt="image" src="https://github.com/user-attachments/assets/4e8505d6-5687-4305-9514-03d31c1ebe25" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
