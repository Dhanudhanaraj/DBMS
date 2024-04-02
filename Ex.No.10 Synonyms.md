# EXP NO 10: SYNONYMS AND ASSERTIONS IN SQL 
### DATE: 
## AIM:
To create a student database and create a synonym and assertions.

## THEORY
## SYNONYM

A SYNONYM provides another name for database object, referred to as original object, that may exist on a local or another server.

### ASSERTIONS

* An assertion is a piece of SQL which makes sure a condition is satisfied, else or it stops the action being taken on a database.
* An assertion is a constraint that might be dependent upon multiple rows of multiple tables.


## Query:
### 1) Create a table EMPLOYEE and perform insertion of two rows.

### SQL QUERY: 
```
CREATE TABLE EMPLOYEE (
    employee_id INT PRIMARY KEY,
    employee_name VARCHAR(255),
    employee_salary DECIMAL(10, 2)
);

INSERT INTO EMPLOYEE (employee_id, employee_name, employee_salary)
VALUES (1, 'Kayal', 50000.00);

INSERT INTO EMPLOYEE (employee_id, employee_name, employee_salary)
VALUES (2, 'Dolly', 60000.00);
```

### OUTPUT:
![Screenshot 2024-04-02 142931](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/a3baab08-f624-4690-b739-87070a47b9e6)

### 2) Create a synonym S1 for EMPLOYEE  table.

### SQL QUERY: 
```
CREATE SYNONYM S1 FOR EMPLOYEE;
```
### OUTPUT:
![Screenshot 2024-04-02 142949](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/4da68d32-b801-448b-821a-6d33faea53f8)


### 3) Display the EMPLOYEE  table using synonym S1.
 
### SQL QUERY: 
```
SELECT * FROM S1;
```

### OUTPUT:
![Screenshot 2024-04-02 143009](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/963c4290-5e9f-449b-b356-44b806b8cd8b)


### 4) Drop the synonym.

### SQL QUERY: 
```
DROP SYNONYM S1;
```

### OUTPUT:
![Screenshot 2024-04-02 143028](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/4a0abc5f-bcd9-4f06-895f-a4e86c47cb91)



### 5) Create a supplier table and create a sequence S2 for supplier table id.

### SQL QUERY: 
```
CREATE TABLE SUPPLIER (
    supplier_id INT PRIMARY KEY,
    supplier_name VARCHAR(255)
);

CREATE SEQUENCE S2;
```

### OUTPUT:
![Screenshot 2024-04-02 143046](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/e7b66211-5bf4-4293-8d00-53f01a69d27c)


### 6) insert the data into supplier table use sequence.

### SQL QUERY: 
```
INSERT INTO SUPPLIER (supplier_id, supplier_name)
VALUES (S2.NEXTVAL, 'AB Suppliers');

INSERT INTO SUPPLIER (supplier_id, supplier_name)
VALUES (S2.NEXTVAL, 'CD Suppliers');
```

### OUTPUT:
![Screenshot 2024-04-02 143108](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/a592143c-d033-4385-ba95-90edc540ad76)

### 7) Drop the sequence

### SQL QUERY: 
```
DROP SEQUENCE S2;
```

### OUTPUT:
![Screenshot 2024-04-02 143910](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/d9df85ea-cf61-4cfe-adb3-90a65529a68e)

## RESULT :
Thus the sequence and synonym created and used in SQL.
