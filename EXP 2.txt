#Query 

CREATE TABLE EMPLOYEES (
  Employee_id     NUMBER(6)     PRIMARY KEY,
  First_Name      VARCHAR2(20),
  Last_Name       VARCHAR2(25)  NOT NULL,
  Email           VARCHAR2(25)  NOT NULL,
  Phone_Number    VARCHAR2(20),
  Hire_date       DATE          NOT NULL,
  Job_id          VARCHAR2(10)  NOT NULL,
  Salary          NUMBER(8,2),
  Commission_pct  NUMBER(2,2),
  Manager_id      NUMBER(6),
  Department_id   NUMBER(4)
);

#Query 
SELECT Employee_id, First_Name, Last_Name, Salary FROM EMPLOYEES;

#Query 
SELECT * FROM EMPLOYEES WHERE Manager_id = 100;

#Query 
SELECT * FROM EMPLOYEES WHERE Manager_id = 100;

#Query 
SELECT * FROM EMPLOYEES WHERE Salary >= 4800;

#Query 
SELECT * FROM EMPLOYEES WHERE UPPER(Last_Name) = 'AUSTIN';

#Query 
SELECT DISTINCT Manager_id FROM EMPLOYEES;

#Query 
CREATE TABLE EMP (
  EmpNo     NUMBER(5),
  EmpName   VARCHAR2(30),
  Job       VARCHAR2(20),
  Basic     NUMBER(8,2),
  DA        NUMBER(8,2),
  HRA       NUMBER(8,2),
  PF        NUMBER(8,2),
  GrossPay  NUMBER(8,2),
  NetPay    NUMBER(8,2)
);

#Query 
INSERT INTO EMP VALUES (101, 'Ravi', 'Manager', 10000, 10000*0.3, 10000*0.4, 10000*0.1, 10000+10000*0.3+10000*0.4, 10000+10000*0.3+10000*0.4-10000*0.1);
INSERT INTO EMP VALUES (102, 'Priya', 'Clerk', 8000, 8000*0.3, 8000*0.4, 8000*0.1, 8000+8000*0.3+8000*0.4, 8000+8000*0.3+8000*0.4-8000*0.1);
INSERT INTO EMP VALUES (103, 'Kumar', 'Analyst', 9000, 9000*0.3, 9000*0.4, 9000*0.1, 9000+9000*0.3+9000*0.4, 9000+9000*0.3+9000*0.4-9000*0.1);
INSERT INTO EMP VALUES (104, 'Meena', 'Salesman', 7000, 7000*0.3, 7000*0.4, 7000*0.1, 7000+7000*0.3+7000*0.4, 7000+7000*0.3+7000*0.4-7000*0.1);
INSERT INTO EMP VALUES (105, 'Arun', 'Clerk', 6000, 6000*0.3, 6000*0.4, 6000*0.1, 6000+6000*0.3+6000*0.4, 6000+6000*0.3+6000*0.4-6000*0.1);

#Query 
SELECT * FROM EMP E
WHERE Basic = (
  SELECT MIN(Basic)
  FROM EMP
  WHERE Job = E.Job
);
