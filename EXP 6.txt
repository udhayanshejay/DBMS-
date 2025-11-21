#Query
SELECT E.Employee_id, E.First_name, E.Last_name, D.Dept_name
FROM EMPLOYEES E
JOIN DEPARTMENT D ON E.Department_id = D.Dept_id;

#Query
SELECT E.Employee_id, E.First_name, D.Dept_name
FROM EMPLOYEES E
LEFT JOIN DEPARTMENT D ON E.Department_id = D.Dept_id;

#Query
SELECT E.Employee_id, E.First_name, D.Dept_name
FROM EMPLOYEES E
RIGHT JOIN DEPARTMENT D ON E.Department_id = D.Dept_id;

#Query
SELECT E.Employee_id, E.First_name, D.Dept_name
FROM EMPLOYEES E
FULL OUTER JOIN DEPARTMENT D ON E.Department_id = D.Dept_id;

#Query
SELECT E.Employee_id, E.First_name, M.First_name AS Manager_Name
FROM EMPLOYEES E
JOIN EMPLOYEES M ON E.Manager_id = M.Employee_id;

#Query
SELECT First_name, Last_name, Salary
FROM EMPLOYEES
WHERE Salary > (SELECT AVG(Salary) FROM EMPLOYEES);

#Query
SELECT First_name, Last_name
FROM EMPLOYEES
WHERE Department_id = (
  SELECT Department_id
  FROM EMPLOYEES
  WHERE First_name = 'Steven'
);

#Query
SELECT E.Employee_id, E.First_name, E.Salary, E.Department_id
FROM EMPLOYEES E
WHERE E.Salary = (
  SELECT MAX(Salary)
  FROM EMPLOYEES
  WHERE Department_id = E.Department_id
);
