#Query
SELECT COUNT(*) AS Total_Employees
FROM EMPLOYEES;

#Query
SELECT 
  MAX(Salary) AS Max_Salary,
  MIN(Salary) AS Min_Salary,
  AVG(Salary) AS Avg_Salary,
  SUM(Salary) AS Total_Salary
FROM EMPLOYEES;

#Query
SELECT Department_id, COUNT(*) AS Dept_Count
FROM EMPLOYEES
GROUP BY Department_id;

#Query
SELECT Job_id, AVG(Salary) AS Avg_Salary
FROM EMPLOYEES
GROUP BY Job_id;

#Query
SELECT Department_id, SUM(Salary) AS Total_Salary
FROM EMPLOYEES
GROUP BY Department_id
HAVING COUNT(*) > 3;

#Query
SELECT Department_id, AVG(Salary) AS Avg_Salary
FROM EMPLOYEES
GROUP BY Department_id
HAVING AVG(Salary) > 5000;

#Query
SELECT Job_id, COUNT(*) AS Job_Count
FROM EMPLOYEES
GROUP BY Job_id;
