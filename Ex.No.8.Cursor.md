# Ex. No: 8 PL/SQL program using Cursor 
### DATE: 
### AIM: To create PL/SQL program to display the customer table 

### Steps:
1. Declare the variable  in Declare section.
2. Fetch the variable with datatype similar to data type in cursor 
3. Create a cursor to select all rows from customers table.
4. Display the result 
5. End the begin section.

### Program:
#### Create employee table:
```
CREATE TABLE customer (
  customerid NUMBER,
  customername VARCHAR(10),
  dept VARCHAR(10),
  salary NUMBER
);

INSERT INTO customer VALUES (1, 'Dhanu', 'HR', 100000);
INSERT INTO customer VALUES (2, 'Amutha', 'Staff', 80000);
select * from customer;
```

### Output:
![Screenshot 2024-04-20 184243](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/054334e8-af9b-42be-94e5-d5467e542b94)

#### PLSQL Cursor code:
```
DECLARE
   CURSOR customer_cursor IS
   SELECT customerid,customername,dept,salary
   FROM customer;
   customer_id NUMBER;
   customer_name VARCHAR(50);
   customer_dept VARCHAR(50);
   customer_salary NUMBER;
BEGIN
  OPEN customer_cursor;

  LOOP
    FETCH customer_cursor INTO customer_id, customer_name, customer_dept, customer_salary;

    EXIT WHEN customer_cursor%NOTFOUND;

    DBMS_OUTPUT.PUT_LINE('Customer ID: ' || customer_id);
    DBMS_OUTPUT.PUT_LINE('Customer Name: ' || customer_name);
    DBMS_OUTPUT.PUT_LINE('Department: ' || customer_dept);
    DBMS_OUTPUT.PUT_LINE('Salary: ' || customer_salary);
  END LOOP;

  CLOSE customer_cursor;
END;
```
### Output:
![Screenshot 2024-04-20 184340](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/d949bec1-f099-4873-b011-c60348b573d7)

### Result:
Thust the program was performed sucessfully.
