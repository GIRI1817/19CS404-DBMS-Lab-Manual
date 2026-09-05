# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.
```sql
select o.ord_no,o.purch_amt,c.cust_name,c.city 
from orders as o  
join customer as c
on o.customer_id=c.customer_id
where o.purch_amt between 500 and 2000;
```

**Output:**

<img width="1230" height="499" alt="image" src="https://github.com/user-attachments/assets/26b7b28b-bc14-4ca0-8d08-d191a8ac7999" />

**Question 2**
---
Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned.
```sql
SELECT 
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    c.cust_name,
    c.city AS customer_city,
    c.grade,
    s.name AS salesman_name,
    s.city AS salesman_city,
    s.commission
FROM 
    orders AS o
JOIN 
    customer AS c 
    ON o.customer_id = c.customer_id
JOIN 
    salesman AS s 
    ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="1335" height="650" alt="image" src="https://github.com/user-attachments/assets/cebe8d2a-0ed0-4163-9895-17f6fffe9980" />

**Question 3**
---
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and a condition filtering for test results with a test date between '2024-03-01' and '2024-03-31'.
```sql
select 
p.patient_id,
p.first_name,
p.last_name,
p.date_of_birth,
p.admission_date,
p.discharge_date,
p.doctor_id
from patients as p
inner join test_results as t
on p.patient_id=t.patient_id
where t.test_date between '2024-03-01' and '2024-03-31';
```

**Output:**

<img width="1112" height="238" alt="image" src="https://github.com/user-attachments/assets/08950d2b-0a16-4985-bba2-845282be55dd" />

**Question 4**
---
From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.
```sql
select
c.cust_name as 'Customer Name',
c.city,
s.name as 'Salesman',
s.commission
from customer as c
join salesman as s
on c.salesman_id=s.salesman_id;
```

**Output:**

<img width="688" height="508" alt="image" src="https://github.com/user-attachments/assets/f6b87023-103c-42b3-9cad-4a40fc84559d" />

**Question 5**
---
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and a condition filtering for appointments with an appointment date between '2024-02-01' and '2024-02-28'.
```sql
select 
p.patient_id,
p.first_name,
p.last_name,
p.date_of_birth,
p.admission_date,
p.discharge_date,
p.doctor_id
from patients as p
inner join appointments as a
on p.patient_id=a.patient_id
where a.appointment_date between '2024-02-01' and '2024-02-28';
```

**Output:**

<img width="1073" height="233" alt="image" src="https://github.com/user-attachments/assets/49cfca6f-ef93-4588-9f73-79c09028c251" />

**Question 6**
---
From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.
```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city ,
    s.name AS Salesman,
    s.commission
FROM 
    customer AS c
JOIN 
    salesman AS s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    s.commission > 0.12;
```

**Output:**

<img width="689" height="428" alt="image" src="https://github.com/user-attachments/assets/2ff84293-a7a6-4eff-a8ae-54075ec29e59" />

**Question 7**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the test name from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column.
```sql
SELECT 
    p.first_name AS patient_name,
    t.test_name
FROM 
    patients AS p
INNER JOIN 
    test_results AS t
ON 
    p.patient_id = t.patient_id;
```

**Output:**

<img width="460" height="315" alt="image" src="https://github.com/user-attachments/assets/e3fb904a-6c63-4585-8acd-a3d192c6b575" />

**Question 8**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesman_id values that have more than one associated customer.
```sql
SELECT 
    s.name,
    c.cust_name,
    c.city,
    c.grade,
    c.salesman_id
FROM salesman AS s
LEFT JOIN customer AS c
ON s.salesman_id = c.salesman_id
WHERE c.salesman_id IN (
        SELECT c.salesman_id
        FROM customer as c
        GROUP BY salesman_id
        HAVING COUNT(customer_id) > 1)
ORDER BY s.name, c.grade;
```

**Output:**

<img width="838" height="353" alt="image" src="https://github.com/user-attachments/assets/fef3ab6d-77c3-4ecc-89dc-b18f1225e180" />

**Question 9**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for customers with a grade less than or equal to 100.
```sql
SELECT 
    s.name,
    c.cust_name,
    c.city,
    c.grade,
    c.salesman_id
FROM salesman AS s
LEFT JOIN customer AS c
ON s.salesman_id = c.salesman_id
WHERE c.grade <= 100;
```

**Output:**

<img width="867" height="326" alt="image" src="https://github.com/user-attachments/assets/88ad6c62-530b-4510-908e-39928df0bd83" />

**Question 10**
---
From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.
```sql
SELECT 
    c.cust_name,
    c.city,
    c.grade,
    s.name AS Salesman,
    s.city 
FROM customer AS c
JOIN salesman AS s
ON c.salesman_id = s.salesman_id
ORDER BY c.customer_id ASC;
```

**Output:**

<img width="833" height="504" alt="image" src="https://github.com/user-attachments/assets/581b52bd-4f10-458d-957b-55b9581cdcc4" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
