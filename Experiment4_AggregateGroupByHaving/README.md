# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
What is the average dosage prescribed for each medication?
```sql
select medication,avg(dosage) as AvgDosage 
from Prescriptions 
group by medication;
```

**Output:**

<img width="629" height="827" alt="image" src="https://github.com/user-attachments/assets/47558779-5186-4a78-b24d-c7fa9c0e2c44" />

**Question 2**
---
How many prescriptions were written in each frequency category (e.g., once daily, twice daily)?
```sql
select frequency,count(PrescriptionID) as TotalPrescriptions
from Prescriptions
group by frequency;
```

**Output:**

<img width="758" height="598" alt="image" src="https://github.com/user-attachments/assets/adfde2b2-7cd2-4c02-b230-1ce31c0682a9" />

**Question 3**
---
How many medical records are there for each patient?
```sql
select PatientID,count(RecordID) as TotalRecords
from MedicalRecords
group by PatientID;
```

**Output:**

<img width="597" height="732" alt="image" src="https://github.com/user-attachments/assets/66cfa133-0437-42fa-be98-97f96fc642c2" />

**Question 4**
---
Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.
```sql
select count(*) as COUNT from customer
where city != "Noida";
```

**Output:**

<img width="382" height="397" alt="image" src="https://github.com/user-attachments/assets/de62a518-4be3-4f38-8303-f37913914431" />

**Question 5**
---
Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.
```sql
select sum(purch_amt) as TOTAL from orders;
```

**Output:**

<img width="356" height="377" alt="image" src="https://github.com/user-attachments/assets/f50730b1-089b-429a-9dec-d3b2efe0ea76" />

**Question 6**
---
Write a SQL query to Calculate the average income of the employees with names starting with 'A':
```sql
select avg(income) as avg_income from employee
where name like "A%";
```

**Output:**

<img width="368" height="377" alt="image" src="https://github.com/user-attachments/assets/f07964e1-bbda-4d25-b067-f7d85b3a67f7" />

**Question 7**
---
Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.
```sql
select avg(purch_amt) as AVERAGE from orders;
```

**Output:**

<img width="352" height="380" alt="image" src="https://github.com/user-attachments/assets/7d312a43-9a61-4db4-aa3d-6f411ed01762" />

**Question 8**
---
Write the SQL query that achieves the grouping of data by city, calculates the average income for each city, and includes only those cities where the average income is greater than 500,000.
```sql
select city,AVG(income)
from employee
group by city
having avg(income)>500000;
```

**Output:**

<img width="607" height="508" alt="image" src="https://github.com/user-attachments/assets/8b732a45-b149-46c5-a44b-1e6733e40745" />

**Question 9**
---
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 400,000.
```sql
select age,MIN(income) from employee
group by age
having min(income)<400000;
```

**Output:**

<img width="581" height="451" alt="image" src="https://github.com/user-attachments/assets/bf8231bc-5526-4d9a-b7f1-bfb56b17efd5" />

**Question 10**
---
Write the SQL query that accomplishes the selection of product which has lowest price in each category from the "products" table and includes only those products where the minimum price is less than 10.
```sql
select category_id,min(price) as Price from products
group by category_id
having min(price)<10;
```

**Output:**

<img width="653" height="454" alt="image" src="https://github.com/user-attachments/assets/1e474d7f-de9f-4ec3-ac8f-603120cfd0f0" />
<img width="1872" height="863" alt="image" src="https://github.com/user-attachments/assets/8846be84-763e-4887-966b-65ba6036113d" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
