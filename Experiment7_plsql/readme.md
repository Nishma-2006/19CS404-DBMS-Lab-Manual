# Experiment 7: PL/SQL – Variables, Control Structures and Loops

# NAME: Nishma Sherin .K
# REG NO : 212224240104

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
### program
```sql
DECLARE
    num1 NUMBER := 80;   -- First number
    num2 NUMBER := 40;   -- Second number
BEGIN
    IF num1 > num2 THEN
        DBMS_OUTPUT.PUT_LINE('Greatest number is: ' || num1);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Greatest number is: ' || num2);
    END IF;
END;
/
```
### output

<img width="628" height="120" alt="image" src="https://github.com/user-attachments/assets/05278463-b1b7-4528-9e4b-78d8e46a4ee1" />

---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Sum of first 10 natural numbers is: 55
### program
```sql
DECLARE
    n NUMBER := 10;     -- Value of N
    i NUMBER := 1;      -- Counter variable
    sum NUMBER := 0;    -- Initialize sum
BEGIN
    WHILE i <= n LOOP
        sum := sum + i; -- Add current number to sum
        i := i + 1;     -- Increment counter
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
END;

```
### output

<img width="819" height="140" alt="image" src="https://github.com/user-attachments/assets/0642b3c4-de5d-404c-8f1f-9ee50c018c92" />

---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8
### program
```sql
SET SERVEROUTPUT ON;
DECLARE
    num NUMBER := &n;
    a NUMBER := 0;
    b NUMBER := 1;
    c NUMBER;
    i NUMBER := 3;
BEGIN
    DBMS_OUTPUT.PUT_LINE('n = ' || num);
    DBMS_OUTPUT.PUT('Fibonacci sequence: ' || a || ', ' || b);

    WHILE i <= num LOOP
        c := a + b;
        DBMS_OUTPUT.PUT(', ' || c);
        a := b;
        b := c;
        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.NEW_LINE;
END;


```
### output
<img width="665" height="149" alt="image" src="https://github.com/user-attachments/assets/5331c448-efb9-4be7-8ec4-adb686f227bf" />

---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

**Expected Output:**  
n = 1535  
Reversed number is 5351
### program
```sql
DECLARE
    n NUMBER := 1535;
    remainder NUMBER;
    reverse_num NUMBER := 0;
BEGIN
    WHILE n > 0 LOOP
        remainder := MOD(n,10);
        reverse_num := reverse_num * 10 + remainder;
        n := TRUNC(n/10);
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Reversed number is ' || reverse_num);
END;
```
### output

<img width="760" height="142" alt="image" src="https://github.com/user-attachments/assets/3ca793cc-a2a4-40f5-b084-d477184a645c" />

---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15
### program
```sql
DECLARE
    a NUMBER := 10;
    b NUMBER := 9;
    c NUMBER := 15;
BEGIN
    IF a > b AND a > c THEN
        DBMS_OUTPUT.PUT_LINE('Largest number is ' || a);
    ELSIF b > a AND b > c THEN
        DBMS_OUTPUT.PUT_LINE('Largest number is ' || b);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Largest number is ' || c);
    END IF;
END;

```
### output

<img width="852" height="138" alt="image" src="https://github.com/user-attachments/assets/b58bf830-df6b-42dd-a671-43c5b2d0f788" />

## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
