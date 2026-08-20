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
Write a SQL statement to increase the salary of employees under the department 40, 90 and 110 according to the company rules. Salary will be increased by 25% for the department 40, 15% for department 90 and 10% for the department 110 and the rest of the departments will remain same.
```sql
update Employees
set salary=
    case
        when department_id=40 then round(salary*1.25 )
        when department_id=90 then round(salary*1.15 )
        when department_id=110 then round(salary*1.1 )
        else salary
    end;
```

**Output:**

<img width="1173" height="265" alt="image" src="https://github.com/user-attachments/assets/ca846cb1-9566-41d1-a3ac-265bfa1892d8" />

**Question 2**
---
Write a SQL statement to double the availability of the product with product_id 1.
```sql
update products
set availability=2*availability
where product_id=1;
```

**Output:**

<img width="976" height="220" alt="image" src="https://github.com/user-attachments/assets/c93cccfc-bf2f-4b1c-a5bc-245eae6f08a8" />

**Question 3**
---
Write a SQL statement to Increase the selling price by 15% in the products table where quantity in stock is less than 50 and supplier ID is 10.
```sql
update Products
set sell_price=sell_price*1.15
where quantity<50 and  supplier_id=10;
```

**Output:**

<img width="1220" height="293" alt="image" src="https://github.com/user-attachments/assets/bdfed657-f540-4738-91e7-3730490b756e" />

**Question 4**
---
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.
```sql
update Products
set product_name='Premium Bread'
where product_id=5;
```

**Output:**

<img width="1181" height="233" alt="image" src="https://github.com/user-attachments/assets/84ed8a34-0e8a-478e-9f89-d794c3179581" />

**Question 5**
---
Change the supplier name to upper case where contact person contains ' Singh' in suppliers table.
```sql
update suppliers
set supplier_name=upper(supplier_name) 
where contact_person like '%Singh';
```

**Output:**

<img width="1362" height="231" alt="image" src="https://github.com/user-attachments/assets/991813cd-5e25-4002-9df0-e77cb61660e1" />

**Question 6**
---
Write a SQL query to Delete customers with 'GRADE' 3 and whose 'CUST_NAME' contains the substring 'BBB', and 'PAYMENT_AMT' is greater than 2000
```sql
delete from customer
where grade=3 and cust_name like "%BBB%" and PAYMENT_AMT>2000;
```

**Output:**

<img width="1358" height="302" alt="image" src="https://github.com/user-attachments/assets/1a6646f8-5f25-4a95-9045-2ed7d697c6e8" />

**Question 7**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3
```sql
delete from Surgeries
where surgery_id=3;
```

**Output:**

<img width="655" height="233" alt="image" src="https://github.com/user-attachments/assets/a860df70-cf38-4cc4-adc0-35c772542016" />

**Question 8**
---
Write a SQL query to delete a specific doctor from Doctors table whose ID is 1.
```sql
delete from doctors
where doctor_id=1;
```

**Output:**

<img width="710" height="172" alt="image" src="https://github.com/user-attachments/assets/0395e159-3901-4141-adaf-9d1a5b87bbeb" />

**Question 9**
---
Write a SQL query to Delete customers whose 'GRADE' is greater than 2 and have a 'PAYMENT_AMT' less than the average 'PAYMENT_AMT' for all customers, or whose 'OUTSTANDING_AMT' is greater than 8000.
```sql
delete from customer
where grade>2 and payment_amt<(select avg(payment_amt) from customer) or outstanding_amt>8000;
```

**Output:**

<img width="1448" height="339" alt="image" src="https://github.com/user-attachments/assets/74794e3d-4045-425d-9b12-13def1e2f017" />

**Question 10**
---
Write a SQL query to Delete All Doctors with a NULL Specialization
```sql
delete from doctors
where specialization is null;
```

**Output:**

<img width="609" height="517" alt="image" src="https://github.com/user-attachments/assets/a484e376-3b93-44ee-b993-59f81f6cda17" />

<img width="1918" height="1197" alt="image" src="https://github.com/user-attachments/assets/7eb07df0-35a0-4255-8e07-3b20a8dc9369" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
