#Query
ALTER TABLE EMP
ADD CONSTRAINT my_emp_id_pk PRIMARY KEY (ID);

#Query
ALTER TABLE DEPT
ADD CONSTRAINT my_dept_id_pk PRIMARY KEY (ID);

#Query
ALTER TABLE EMP
ADD DEPT_ID NUMBER(7);

#Query
ALTER TABLE EMP
ADD CONSTRAINT my_emp_dept_id_fk FOREIGN KEY (DEPT_ID)
REFERENCES DEPT(ID);

#Query
ALTER TABLE EMP
ADD COMMISSION NUMBER(2,2)
CONSTRAINT emp_comm_check CHECK (COMMISSION > 0);

#Query
SELECT constraint_name, constraint_type, search_condition
FROM user_constraints
WHERE table_name = 'EMP';

#Query
SELECT constraint_name, column_name
FROM user_cons_columns
WHERE table_name = 'EMP';
