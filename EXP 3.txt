#Query
SELECT employee_id, last_name, sal*12 AS "ANNUAL SALARY"
FROM employees;

#Query
SELECT employee_id, last_name, sal*12 AS "ANNUAL SALARY"
FROM employees;

#Query
DESC departments;

SELECT * FROM departments;

#Query
SELECT employee_id, last_name, job_id, hire_date
FROM employees;

#Query
SELECT employee_id, last_name, job_id, hire_date AS STARTDATE
FROM employees;

#Query
SELECT DISTINCT job_id FROM employees;

#Query
SELECT last_name || ', ' || job_id AS "EMPLOYEE and TITLE"
FROM employees;

#Query
SELECT employee_id || ', ' ||
       first_name || ', ' ||
       last_name || ', ' ||
       email || ', ' ||
       phone_number || ', ' ||
       hire_date || ', ' ||
       job_id || ', ' ||
       salary || ', ' ||
       commission_pct || ', ' ||
       manager_id || ', ' ||
       department_id AS "THE_OUTPUT"
FROM employees;
