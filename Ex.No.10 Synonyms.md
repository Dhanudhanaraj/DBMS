# EXP NO 10: SYNONYMS AND ASSERTIONS IN SQL 
### DATE: 
## AIM:
To create a student database and create a synonym and assertions.

## THEORY
## SYNONYM
<div align="justify">
A SYNONYM provides another name for database object, referred to as original object, that may exist on a local or another server.
</div>
## ASSERTIONS
<div align="justify">
* An assertion is a piece of SQL which makes sure a condition is satisfied, else or it stops the action being taken on a database.
* An assertion is a constraint that might be dependent upon multiple rows of multiple tables.
</div>

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

### 2) Create a synonym S1 for EMPLOYEE  table.

### SQL QUERY: 
```
CREATE SYNONYM S1 FOR EMPLOYEE;
```
### OUTPUT:


### 3) Display the EMPLOYEE  table using synonym S1.
 
### SQL QUERY: 
```
SELECT * FROM S1;
```

### OUTPUT:


### 4) Drop the synonym.

### SQL QUERY: 
```
DROP SYNONYM S1;
```

### OUTPUT:



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


### 6) insert the data into supplier table use sequence.

### SQL QUERY: 
```
INSERT INTO SUPPLIER (supplier_id, supplier_name)
VALUES (S2.NEXTVAL, 'AB Suppliers');

INSERT INTO SUPPLIER (supplier_id, supplier_name)
VALUES (S2.NEXTVAL, 'CD Suppliers');
```

### OUTPUT:
### 7) Drop the sequence

### SQL QUERY: 
```
DROP SEQUENCE S2;
```

### OUTPUT:

## RESULT :
Thus the sequence and synonym created and used in SQL.
