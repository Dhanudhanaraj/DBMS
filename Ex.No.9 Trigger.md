# Ex. No: 9 PL/SQL program using Triggers 
### DATE: 
### AIM: 
To create PL/SQL program to display new and old salary of customer when before/ after updation takes place. 

### Steps:
1. Create a trigger for each row when updation occurs.
2. Declare the variable in Declare section.
3. Start the begin section.
4. Calculate the salary changes.
5. Display the result 
6. End the begin section.

### Program:
```
NAME:DHANUMALYA.D
REGISTER NUMBER:212222230030
```
```
create table customers(ID int,NAME varchar(20),AGE int,ADDRESS varchar(20),salary int);
insert into customers values( 1,'Dhanu',32,'Chennai',2000);
insert into customers values( 1,'Amutha',25,'Bangalore',1500);
insert into customers values( 1,'Abirami',23,'Delhi',2000);
DECLARE 
   c_id customers.id%type; 
   c_name customers.name%type; 
   c_addr customers.address%type; 
   CURSOR c_customers is 
      SELECT id, name, address FROM customers; 
BEGIN 
   OPEN c_customers; 
   LOOP 
   FETCH c_customers into c_id, c_name, c_addr; 
      EXIT WHEN c_customers%notfound; 
      dbms_output.put_line(c_id || ' ' || c_name || ' ' || c_addr); 
   END LOOP; 
   CLOSE c_customers; 
END; 
/
```

### Output:
![Screenshot 2024-04-23 153457](https://github.com/Dhanudhanaraj/DBMS/assets/119218812/de6b775f-2908-468c-ac73-88cf4bd37851)

### Result:
Thust the program was performed sucessfully.
