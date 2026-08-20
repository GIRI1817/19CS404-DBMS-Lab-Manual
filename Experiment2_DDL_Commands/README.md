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
Create a table named ProjectAssignments with the following constraints: AssignmentID as INTEGER should be the primary key. EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID). ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID). AssignmentDate as DATE should be NOT NULL.

```sql
create table ProjectAssignments(
   AssignmentID INT PRIMARY KEY,
   EmployeeID INT, 
   ProjectID INT,
   AssignmentDate DATE NOT NULL,
   FOREIGN KEY(EmployeeID) REFERENCES Employees(EmployeeID),
   FOREIGN KEY(ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**

<img width="1104" height="165" alt="image" src="https://github.com/user-attachments/assets/54b41429-ed29-4b54-a8e7-1d454e6fc87c" />

**Question 2**
---
Write a SQL Query to add an attribute designation in the employee table with the data type VARCHAR(50).

```sql
ALTER TABLE employee
ADD COLUMN designation varchar(50);
```

**Output:**

<img width="1178" height="239" alt="image" src="https://github.com/user-attachments/assets/16ecb6f8-83c3-4cf4-99f1-fea17dcdceba" />

**Question 3**
---
Create a new table named contacts with the following specifications: contact_id as INTEGER and primary key. first_name as TEXT and not NULL. last_name as TEXT and not NULL. email as TEXT. phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.
```sql
create table contacts(
   contact_id INT PRIMARY KEY,
   first_name TEXT NOT NULL, 
   last_name TEXT NOT NULL,
   email TEXT,
   phone TEXT NOT NULL CHECK(length(phone)>=10)
);
```

**Output:**

<img width="1321" height="193" alt="image" src="https://github.com/user-attachments/assets/a290160f-7787-42a0-ad22-da4894c6859a" />

**Question 4**
---
Create a table named Orders with the following constraints: OrderID as INTEGER should be the primary key. OrderDate as DATE should be not NULL. CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).
```sql
create table Orders(
   OrderID INT PRIMARY KEY,
   OrderDate DATE NOT NULL, 
   CustomerID INT,
   FOREIGN KEY(CustomerID) REFERENCES Customers(CustomerID)
);
```

**Output:**

<img width="1299" height="232" alt="image" src="https://github.com/user-attachments/assets/125d14b2-e979-4d16-9485-b531e7a4661d" />

**Question 5**
---
Write a SQL query to add a new column MobileNumber of type NUMBER and a new column Address of type VARCHAR(100) to the Student_details table.
```sql
ALTER TABLE Student_details ADD  MobileNumber NUMBER;
ALTER TABLE Student_details ADD Address VARCHAR(100);
```

**Output:**

<img width="1209" height="290" alt="image" src="https://github.com/user-attachments/assets/d78fd96e-6377-4491-a037-bdf34e29e44e" />

**Question 6**
---
Create a table named Products with the following constraints: ProductID as INTEGER should be the primary key. ProductName as TEXT should be unique and not NULL. Price as REAL should be greater than 0. StockQuantity as INTEGER should be non-negative.
```sql
create table  Products(
   ProductID INT PRIMARY KEY,
   ProductName TEXT NOT NULL UNIQUE, 
   Price REAL NOT NULL CHECK(Price>0),
   StockQuantity INT CHECK(StockQuantity>=0)
);
```

**Output:**

<img width="1186" height="182" alt="image" src="https://github.com/user-attachments/assets/1c91e8a0-f126-4704-bbcf-f861fc770e5f" />

**Question 7**
---
Insert a book with ISBN 978-1234567890, Title Data Science Essentials, Author Jane Doe, Publisher TechBooks, and Year 2024 into the Books table.
```sql
INSERT INTO Books(ISBN,Title,Author,Publisher,Year) VALUES ("978-1234567890","Data Science Essentials","Jane Doe","TechBooks","2024");
```

**Output:**

<img width="1212" height="209" alt="image" src="https://github.com/user-attachments/assets/e32ae219-0ab1-47c3-bd63-2f96cd15c618" />

**Question 8**
---
Create a table named Departments with the following columns: DepartmentID as INTEGER DepartmentName as TEXT
```sql
CREATE TABLE Departments(
  DepartmentID INTEGER,
  DepartmentName TEXT
);
```

**Output:**

<img width="1226" height="275" alt="image" src="https://github.com/user-attachments/assets/bfcefc46-9279-4396-be77-4f7771736e51" />

**Question 9**
---
In the Student_details table, insert a student record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.
```sql
INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS) VALUES (205,"Olivia Green","F",NULL,NULL);
INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS) VALUES (207,"Liam Smith","M","Mathematic",85);
INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS) VALUES (208,"Sophia Johns","F","Science",NULL);
```

**Output:**

<img width="1141" height="230" alt="image" src="https://github.com/user-attachments/assets/6d2ce67d-b1c2-45eb-83b0-89239105eb5b" />

**Question 10**
---
Insert all products from Discontinued_products into Products. Table attributes are ProductID, ProductName, Price, Stock
```sql
INSERT INTO Products(ProductID,ProductName,Price,Stock)
SELECT ProductID,ProductName,Price,Stock from Discontinued_products;
```

**Output:**
<img width="904" height="233" alt="image" src="https://github.com/user-attachments/assets/72b91d17-83ab-4eed-a285-a83a81013bfc" />

<img width="1917" height="1193" alt="image" src="https://github.com/user-attachments/assets/cf81596e-01e7-4467-854c-8c1ec4014840" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
