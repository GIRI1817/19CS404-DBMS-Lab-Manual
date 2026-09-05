# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Greater number is: 80

## PROGRAM:
```

DECLARE
    a NUMBER := 80;
    b NUMBER := 50;
BEGIN
    IF a > b THEN
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || a);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || b);
    END IF;
END;
/
```
## OUTPUT:
<img width="902" height="861" alt="image" src="https://github.com/user-attachments/assets/286fa27f-1f9f-485c-b429-4f64596c60ba" />

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Sum of first 10 natural numbers is: 55

## PROGRAM:
```

DECLARE
    n NUMBER := 10;
    i NUMBER := 1;
    s NUMBER := 0;
BEGIN
    WHILE i <= n LOOP
        s := s + i;
        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Sum of first 10 natural numbers is: ' || s);
END;
/
```
## OUTPUT:
<img width="892" height="871" alt="image" src="https://github.com/user-attachments/assets/05fec5ee-6094-4434-98b9-cee1654f5731" />

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

## PROGRAM:
```

DECLARE
    n NUMBER := 7;
    a NUMBER := 0;
    b NUMBER := 1;
    c NUMBER;
    i NUMBER := 3;
BEGIN
    DBMS_OUTPUT.PUT_LINE('Fibonacci sequence:');
    DBMS_OUTPUT.PUT_LINE(a);
    DBMS_OUTPUT.PUT_LINE(b);

    WHILE i <= n LOOP
        c := a + b;
        DBMS_OUTPUT.PUT_LINE(c);

        a := b;
        b := c;

        i := i + 1;
    END LOOP;
END;
/
```
## OUTPUT:
<img width="860" height="844" alt="image" src="https://github.com/user-attachments/assets/b26d5f09-b436-42ca-9dd0-0d1341583fc3" />

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

**Expected Output:**  
n = 1535  
Reversed number is 5351

## PROGRAM:
```

DECLARE
    n NUMBER := 1535;
    rev NUMBER := 0;
    rem NUMBER;
    temp NUMBER;
BEGIN
    temp := n;

    WHILE temp > 0 LOOP
        rem := MOD(temp,10);
        rev := rev * 10 + rem;
        temp := TRUNC(temp/10);
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Reversed number is ' || rev);
END;
/
```
## OUTPUT:
<img width="852" height="850" alt="image" src="https://github.com/user-attachments/assets/51113a82-5049-42b6-9543-4fa9069aba79" />

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

## PROGRAM:
```

DECLARE
    a NUMBER := 10;
    b NUMBER := 9;
    c NUMBER := 15;
BEGIN
    IF a > b AND a > c THEN
        DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || a);

    ELSIF b > a AND b > c THEN
        DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || b);

    ELSE
        DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || c);
    END IF;
END;
/
```
## OUTPUT:
<img width="817" height="846" alt="image" src="https://github.com/user-attachments/assets/9aa885af-d5d1-4e29-9d7a-c4cda5c4f8c4" />


## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
