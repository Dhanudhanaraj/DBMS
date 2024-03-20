# Ex. No: 6 PL/SQL program to perform addition and subtraction of two number 
### DATE: 
### AIM:
To create PL/SQL program to perform addition and subtraction of two number.

### Steps:
1. Declare the variable a, b and necessary variables in Declare section.
2. Perform addition of two numbers
3. Perform subtraction of two numbers 
4. Display the result 
5. End the begin section.

### Program:
```
DECLARE
 a NUMBER := 100;
 b NUMBER := 50;
 c NUMBER;
BEGIN
 c:=a+b;
 dbms_output.Put_line('addition of two numbers is '||c);
 c:=a-b;
 dbms_output.Put_line('subtraction of two numbers is '||c);
END; 

```

### Output:
![Screenshot 2024-03-20 113629](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/020abeb8-7dde-4885-aff8-dab806ec7240)


### Result:
Thust the program was performed sucessfully.
