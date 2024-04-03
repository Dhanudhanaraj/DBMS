# Ex. No: 6 PL/SQL program -BIGGEST OF THREE NUMBERS  
### DATE: 
### AIM: 
To create PL/SQL program to find biggest of three numbers.

### ALGORITHM:
1. Declare the variable a, b, c and assign value in Declare section.
2. begin the section
3. Find biggest of three numbers 
4. 5. Display the result 
6. End the begin section.

### Program:
```
NAME:DHANUMALYA.D
REGISTER NUMBER:212222230030
```
```
DECLARE
 a NUMBER := 95;
 b NUMBER := 85;
 c NUMBER := 75;
BEGIN
 IF a > b AND a > c THEN
 dbms_output.Put_line('Biggest number is '||a);
 ELSIF b > a AND b > c THEN
 dbms_output.Put_line('Biggest number is '||b);
 ELSE
 dbms_output.Put_line('Biggest number is '||c);
 END IF;
END;
```

### Output:
![Screenshot 2024-04-03 120736](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/4c4d54b0-b1f1-4bad-be3f-d50e47a589dc)

### Result:
Thust the program was performed sucessfully.
