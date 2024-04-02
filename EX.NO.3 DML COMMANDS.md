# EX.NO:3 Data Manipulation Language (DML) Commands and built in functions in SQL
## AIM:
To create a manager database and execute DML queries using SQL.

# THEORY
## DML(Data Manipulation Language)
*  The SQL commands that deal with the manipulation of data present in the database belong to DML or Data Manipulation Language and this includes most of the SQL statements.
*  It is the component of the SQL statement that controls access to data and to the database. Basically, DCL statements are grouped with DML statements.

## List of DML commands: 
1. INSERT: It is used to insert data into a table.
2. UPDATE: It is used to update existing data within a table.
3. DELETE: It is used to delete records from a database table.
4. SELECT: The SELECT command shows the records of the specified table.

## Create the table as given below:
```sql
create table manager(enumber number(6),ename char(15),salary number(5),commission number(4),annualsalary number(7),Hiredate date,designation char(10),deptno number(2),reporting char(10));
```
## insert the following values into the table
```sql
insert into manager values(7369,'Dharsan',2500,500,30000,'30-June-81','clerk',10,'John');
insert into manager values(7839,'Subu',3000,400,36000,'1-Jul-82','manager',null,'James');
insert into manager values(7934,'Aadhi',3500,300,42000,'1-May-82','manager',30,NULL);
insert into manager values(7788,'Vikash',4000,0,48000,'12-Aug-82','clerk',50,'Bond');
```

### Q1) Update all the records of manager table by increasing 10% of their salary as bonus.

### QUERY:
```
update manager 
set salary = salary + (salary * 10/100)
```
### OUTPUT:
![Screenshot 2024-03-18 001458](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/c6714427-2090-4951-bb65-667c07344ffa)


### Q2) Delete the records from manager table where the salary less than 2750.


### QUERY:
```
delete from manager 
where salary < 2750
```

### OUTPUT:
![Screenshot 2024-03-18 001512](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/c65ecf59-fba6-422f-bf9c-84c2dadba197)

### Q3) Display each name of the employee as “Name” and annual salary as “Annual Salary” (Note: Salary in emp table is the monthly salary)


### QUERY:
```
select ename as "Name",salary*12 as annualsalary from manager;
```

### OUTPUT:
![Screenshot 2024-03-18 001534](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/75fb8c3b-a485-4174-9888-0fd622ecb82a)

### Q4)	List the names of Clerks from emp table.


### QUERY:
```
select ename from manager where designation = 'clerk';
```

### OUTPUT:
![Screenshot 2024-03-18 001651](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/ccc091c5-65b4-43db-8f74-17bab4a433d1)


### Q5)	List the names of employee who are not Managers.


### QUERY:
```
select ename from manager where designation != 'manager';
```

### OUTPUT:
![Screenshot 2024-03-18 001651](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/72f8975f-2f6e-4abb-a688-ab612e3df4f5)


### Q6)	List the names of employees not eligible for commission.


### QUERY:
```
select ename from manager where commission = 0;
```

### OUTPUT:
![Screenshot 2024-03-18 001706](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/6c1c5939-9073-4632-9904-23246e08d3cf)


### Q7)	List employees whose name either start or end with ‘s’.


### QUERY:
```
select ename from manager where ename like 'S%' or ename like '%S';
```

### OUTPUT:
![Screenshot 2024-03-18 001722](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/e522bf62-0189-4fe8-91ae-17fa69382d4f)


### Q8) Sort emp table in ascending order by hire-date and list ename, job, deptno and hire-date.


### QUERY:
```
select Hiredate,ename,designation,deptno from manager order by Hiredate;
```

### OUTPUT:
![Screenshot 2024-03-18 001749](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/b355e5b4-aa7e-497c-8ed0-1b94c445728d)


### Q9) List the Details of Employees who have joined before 30 Sept 81.


### QUERY:
```
select * from manager where hiredate<to_date('1981-09-30','YYYY-MM-DD');
```

### OUTPUT:
![Screenshot 2024-03-18 001820](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/34ed9b88-ecb3-47e5-8e1d-a4c0c882b429)


### Q10)	List ename, deptno and sal after sorting emp table in ascending order by deptno and then descending order by sal.


### QUERY:
```

select ename,deptno,salary from manager order by deptno,salary desc;
```

### OUTPUT:
![Screenshot 2024-03-18 001842](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/38334474-b173-4914-94f6-fac2731130bd)


### Q11) List the names of employees not belonging to dept no 30,40 & 10


### QUERY:
```

select ename from manager where deptno != 30 and deptno != 40 and deptno != 10;
```

### OUTPUT:
![Screenshot 2024-03-18 001900](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/89f16adb-562c-4624-8313-33908998a737)

### Q12) Find number of rows in the table EMP

### QUERY:
```

select count (*) as count_ename from manager;
```

### OUTPUT:
![Screenshot 2024-03-18 001913](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/12cce17d-9bb4-4aa9-9d05-2c90d96ead22)


### Q13) Find maximum, minimum and average salary in EMP table.

### QUERY:
```
select avg(salary) as tot_salary from manager;
select min(salary) as min_salary from manager;
select max(salary) as max_salary from manager;
```

### OUTPUT:
![Screenshot 2024-03-18 001935](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/e4369dd1-dd1b-4949-89ae-9f71b68f4b86)

![Screenshot 2024-03-18 001939](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/7b249b51-3330-49a4-b111-48355114f5be)

![Screenshot 2024-03-18 001943](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/31df707d-7bec-40e6-b776-c3dabe34e221)

### Q14) List the jobs and number of employees in each job. The result should be in the descending order of the number of employees.

### QUERY:
```
select designation,enumber from manager order by designation ,enumber desc;
```

### OUTPUT:
![Screenshot 2024-03-18 002045](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/df59fb01-54b9-4856-adea-b4bfa4adb93a)


## RESULT :
Thus the basic DML commands are executed.
