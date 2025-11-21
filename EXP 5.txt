#Query
CREATE VIEW EMPVU80 AS
SELECT * FROM EMPLOYEES
WHERE Department_id = 80;

#Query
CREATE VIEW EMP_SALARY_VIEW AS
SELECT Employee_id AS ID,
       First_name AS FirstName,
       Last_name AS LastName,
       Salary AS MonthlySalary
FROM EMPLOYEES;

#Query
CREATE OR REPLACE VIEW EMP_DEPT10_VIEW AS
SELECT * FROM EMPLOYEES
WHERE Department_id = 10
WITH CHECK OPTION;


#Query
CREATE OR REPLACE VIEW EMP_READONLY_VIEW AS
SELECT Employee_id, First_name, Last_name, Salary
FROM EMPLOYEES
WITH READ ONLY;


#Query
SELECT * FROM EMPVU80;

#Query
INSERT INTO EMPVU80 (Employee_id, First_name, Last_name, Email, Hire_date, Job_id, Salary, Department_id)
VALUES (301, 'John', 'Doe', 'jdoe@example.com', SYSDATE, 'SA_REP', 5000, 80);

#Query
UPDATE EMPVU80
SET Salary = Salary + 500
WHERE Employee_id = 301;

#Query
DELETE FROM EMPVU80
WHERE Employee_id = 301;


#Query
DELETE FROM EMPVU80
WHERE Employee_id = 301;
