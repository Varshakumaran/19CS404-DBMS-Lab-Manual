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

---
## code:
```
DECLARE
    a NUMBER := 20;
    b NUMBER := 15;
BEGIN
    IF a > b THEN
        DBMS_OUTPUT.PUT_LINE('Greatest number is: ' || a);
    ELSIF b > a THEN
        DBMS_OUTPUT.PUT_LINE('Greatest number is: ' || b);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Both numbers are equal');
    END IF;
END;
/

```
## output :

<img width="1920" height="968" alt="ex7 1" src="https://github.com/user-attachments/assets/62f6c537-a515-44ee-8a02-7b44699a6552" />

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Sum of first 10 natural numbers is: 55

---
## code 
```
DECLARE
    n NUMBER := 10;
    sum NUMBER := 0;
    i NUMBER := 1;
BEGIN
    WHILE i <= n LOOP
        sum := sum + i;
        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
END;
/

```
## output
<img width="1912" height="969" alt="ex7 2" src="https://github.com/user-attachments/assets/24fe8ca2-c420-406c-ba3f-bd57b03195d7" />

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

---
## code
```
DECLARE
    n NUMBER := 10;
    a NUMBER := 0;
    b NUMBER := 1;
    c NUMBER;
    i NUMBER := 1;
BEGIN
    DBMS_OUTPUT.PUT_LINE('Fibonacci Series:');

    WHILE i <= n LOOP
        DBMS_OUTPUT.PUT(a || ' ');

        c := a + b;
        a := b;
        b := c;

        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.NEW_LINE;
END;
/

```
## output
<img width="1919" height="966" alt="ex7 3" src="https://github.com/user-attachments/assets/eb86dd99-caf7-4534-9199-e661540d7202" />

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

**Expected Output:**  
n = 1535  
Reversed number is 5351

---
## code
```
DECLARE
    n NUMBER := 12345;
    rev NUMBER := 0;
    digit NUMBER;
BEGIN
    WHILE n > 0 LOOP
        digit := MOD(n, 10);
        rev := rev * 10 + digit;
        n := TRUNC(n / 10);
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Reverse number is: ' || rev);
END;
/
```
## output
<img width="1917" height="970" alt="ex7 4" src="https://github.com/user-attachments/assets/a49a976b-e986-41ed-bcb9-5ee6dee86188" />

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

## code
```
DECLARE
    a NUMBER := 10;
    b NUMBER := 25;
    c NUMBER := 15;
BEGIN
    IF a >= b AND a >= c THEN
        DBMS_OUTPUT.PUT_LINE('Largest number is: ' || a);
    ELSIF b >= a AND b >= c THEN
        DBMS_OUTPUT.PUT_LINE('Largest number is: ' || b);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Largest number is: ' || c);
    END IF;
END;
/
```
## output
<img width="1919" height="973" alt="ex7 5" src="https://github.com/user-attachments/assets/ba9b3319-65f6-4a63-8ac3-c0f63f1a546a" />


## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
