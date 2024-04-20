# EX.NO.4 SubQueries, Views and Joins 
### DATE:
## AIM
To use SubQueries, Views and Joins in SQL 
## Create employee Table
```sql
CREATE TABLE EMP (EMPNO NUMBER(4) PRIMARY KEY,ENAME VARCHAR2(10),JOB VARCHAR2(9),MGR NUMBER(4),HIREDATE DATE,SAL NUMBER(7,2),COMM NUMBER(7,2),DEPTNO NUMBER(2));
```
## Insert the values
```sql
INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7369, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7499, 'ALLEN', 'SALESMAN', 7698, '20-FEB-81', 1600, 300, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7521, 'WARD', 'SALESMAN', 7698, '22-FEB-81', 1250, 500, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7566, 'JONES', 'MANAGER', 7839, '02-APR-81', 2975, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7654, 'MARTIN', 'SALESMAN', 7698, '28-SEP-81', 1250, 1400, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7698, 'BLAKE', 'MANAGER', 7839, '01-MAY-81', 2850, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7782, 'CLARK', 'MANAGER', 7839, '09-JUN-81', 2450, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7788, 'SCOTT', 'ANALYST', 7566, '19-APR-87', 3000, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7839, 'KING', 'PRESIDENT', NULL, '17-NOV-81', 5000, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7844, 'TURNER', 'SALESMAN', 7698, '08-SEP-81', 1500, 0, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7876, 'ADAMS', 'CLERK', 7788, '23-MAY-87', 1100, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7900, 'JAMES', 'CLERK', 7698, '03-DEC-81', 950, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7902, 'FORD', 'ANALYST', 7566, TO_DATE('03-DEC-81', 'DD-MON-RR'), 3000, 20, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7934, 'MILLER', 'CLERK', 7782, TO_DATE('23-JAN-82', 'DD-MON-RR'), 1300, 10, 10);
```

## Create department table
```sql
CREATE TABLE DEPT (DEPTNO NUMBER(2) PRIMARY KEY,DNAME VARCHAR2(14),LOC VARCHAR2(13));
```
## Insert the values in the department table
```sql
INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (10, 'ACCOUNTING', 'NEW YORK');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (20, 'RESEARCH', 'DALLAS');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (30, 'SALES', 'CHICAGO');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (40, 'OPERATIONS', 'BOSTON');
```

### Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.


### QUERY:
```
SELECT ENAME FROM EMP WHERE SAL > (SELECT SAL FROM EMP WHERE EMPNO = 7566);
```

### OUTPUT:
![Screenshot 2024-04-03 111007](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/796f5e8b-1bf4-4acf-8f3b-b61bb96a7d5c)

### Q2) List the ename,job,sal of the employee who get minimum salary in the company.

### QUERY:
```
SELECT ENAME, JOB, SAL FROM EMP WHERE SAL = (SELECT MIN(SAL) FROM EMP);
```

### OUTPUT:
![Screenshot 2024-04-03 111031](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/44925654-eecc-467f-9db7-1490b60620a3)

### Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.

### QUERY:
```
SELECT ENAME, JOB FROM EMP WHERE DEPTNO = 10 AND JOB IN (SELECT JOB FROM EMP WHERE JOB = 'sales');
```

### OUTPUT:
![Screenshot 2024-04-03 111058](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/44abc95f-b0e6-419a-a8e0-4fc6e5d129b8)


### Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.

### QUERY:
```
CREATE VIEW empv5 AS SELECT empno, ename, job FROM EMP WHERE deptno = 10;
SELECT ename FROM empv5;
```

### OUTPUT:
![Screenshot 2024-04-03 111132](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/d7724c58-ff04-44c6-9a4e-ed9810f66641)

### Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.

### QUERY:
```
CREATE VIEW empv30 AS SELECT empno AS "Employee Number", ename AS "Employee Name", sal AS "Salary" FROM EMP WHERE deptno = 30;
SELECT * FROM empv30;
```

### OUTPUT:
![Screenshot 2024-04-03 111158](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/0bcdf331-245a-4a55-864b-d0e990d4bbf7)

### Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table

### QUERY:
```
UPDATE emp SET sal = sal * 1.1 WHERE job = 'CLERK';
SELECT empno, ename, job, sal FROM emp WHERE job = 'CLERK';
```

### OUTPUT:
![Screenshot 2024-04-03 111225](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/6872c8e8-0900-4f8b-bb2d-8586107cdd5c)

## Create a Customer1 Table
```sql
CREATE TABLE Customer1 (customer_id INT,cust_name VARCHAR(20),city VARCHAR(20),grade INT,salesman_id INT);
```
## Inserting Values to the Table
```sql
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3002, 'Nick Rimando', 'New York', 100, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3007, 'Brad Davis', 'New York', 200, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3005, 'Graham Zusi', 'California', 200, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3008, 'Julian Green', 'London', 300, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3004, 'Fabian Johnson', 'Paris', 300, 5006);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3009, 'Geoff Cameron', 'Berlin', 100, 5003);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3003, 'Jozy Altidor', 'Moscow', 200, 5007);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3001, 'Brad Guzan', 'London', NULL, 5005);
```
## Create a Salesperson1 table
```sql
CREATE TABLE Salesman1 (salesman_id INT,name VARCHAR(20),city VARCHAR(20),commission DECIMAL(4,2));
```
## Inserting Values to the Table
```sql
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5001, 'James Hoog', 'New York', 0.15);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5002, 'Nail Knite', 'Paris', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5005, 'Pit Alex', 'London', 0.11);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5006, 'Mc Lyon', 'Paris', 0.14);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5007, 'Paul Adam', 'Rome', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5003, 'Lauson Hen', 'San Jose', 0.12);
```
### Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

### QUERY:
```
SELECT s.name AS Salesman1, c.cust_name, c.city FROM Salesman1 s INNER JOIN Customer1 c ON s.city = c.city;
```

### OUTPUT:
![Screenshot 2024-04-03 111427](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/0f6b67c7-2462-435c-8714-fd002b7e8251)

### Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.


### QUERY:
```
SELECT c.cust_name AS Customer_Name, c.city AS Customer_City, s.name AS Salesman, s.commission FROM Customer1 c JOIN Salesman1 s ON c.salesman_id = s.salesman_id WHERE s.commission > 0.13 ORDER BY s.name ASC;
```

### OUTPUT:
![Screenshot 2024-04-03 111509](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/475bb340-d7d9-49ae-93c3-10bb44e71c7e)

### Q9) Perform Natural join on both tables

### QUERY:
```
SELECT * FROM Salesman1
NATURAL JOIN Customer1;
```

### OUTPUT:
![Screenshot 2024-04-03 111538](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/ff0cd188-d560-4228-96d1-454a11fc4dc0)

### Q10) Perform Left and right join on both tables

### QUERY:
```
SELECT * FROM Customer1
LEFT JOIN Salesman1 ON Customer1.salesman_id = Salesman1.salesman_id;
SELECT * FROM Customer1
RIGHT JOIN Salesman1 ON Customer1.salesman_id = Salesman1.salesman_id;
```

### OUTPUT:
![Screenshot 2024-04-03 111646](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/e9ba77d7-6473-4d50-9464-433454c940ff)

![Screenshot 2024-04-03 111706](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/eac3ef90-7e1c-4b9c-9174-4c4c1b642bf8)

## RESULT 
Thus the basics of subqueries,views,joins are performed in SQL.
