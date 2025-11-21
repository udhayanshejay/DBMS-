#Query
SELECT Employee_id FROM EMPLOYEES
UNION
SELECT EmpNo FROM EMP;

#Query
SELECT Employee_id FROM EMPLOYEES
UNION ALL
SELECT EmpNo FROM EMP;

#Query
SELECT Employee_id FROM EMPLOYEES
INTERSECT
SELECT EmpNo FROM EMP;


#Query
SELECT Employee_id FROM EMPLOYEES
MINUS
SELECT EmpNo FROM EMP;

#Query
SELECT First_name, Last_name, Salary, Department_id
FROM EMPLOYEES E
WHERE Salary > (
  SELECT AVG(Salary)
  FROM EMPLOYEES
  WHERE Department_id = E.Department_id
);


#Query
SELECT First_name, Last_name
FROM EMPLOYEES
WHERE Department_id IN (
  SELECT Dept_id
  FROM DEPARTMENT
  WHERE Location_id IN (
    SELECT Location_id
    FROM LOCATION
    WHERE City = 'NEW YORK'
  )
);


#Query
SELECT Dept_id, Dept_name
FROM DEPARTMENT D
WHERE EXISTS (
  SELECT 1
  FROM EMPLOYEES E
  WHERE E.Department_id = D.Dept_id
);
