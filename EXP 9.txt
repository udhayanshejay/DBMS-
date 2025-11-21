#Query
BEGIN
  DBMS_OUTPUT.PUT_LINE('Welcome to PL/SQL Programming!');
END;

#Query
DECLARE
  v_name VARCHAR2(20) := 'Mohamed';
  v_age  NUMBER := 21;
BEGIN
  DBMS_OUTPUT.PUT_LINE('Name: ' || v_name);
  DBMS_OUTPUT.PUT_LINE('Age: ' || v_age);
END;


#Query
DECLARE
  a NUMBER := 10;
  b NUMBER := 5;
  sum NUMBER;
BEGIN
  sum := a + b;
  DBMS_OUTPUT.PUT_LINE('Sum = ' || sum);
END;

#Query
DECLARE
  marks NUMBER := 85;
BEGIN
  IF marks >= 90 THEN
    DBMS_OUTPUT.PUT_LINE('Grade: A');
  ELSIF marks >= 75 THEN
    DBMS_OUTPUT.PUT_LINE('Grade: B');
  ELSE
    DBMS_OUTPUT.PUT_LINE('Grade: C');
  END IF;
END;


#Query
DECLARE
  i NUMBER := 1;
BEGIN
  LOOP
    DBMS_OUTPUT.PUT_LINE('Iteration: ' || i);
    i := i + 1;
    EXIT WHEN i > 5;
  END LOOP;
END;


#Query
DECLARE
  i NUMBER := 1;
BEGIN
  WHILE i <= 5 LOOP
    DBMS_OUTPUT.PUT_LINE('Count: ' || i);
    i := i + 1;
  END LOOP;
END;


#Query
BEGIN
  FOR i IN 1..5 LOOP
    DBMS_OUTPUT.PUT_LINE('Value: ' || i);
  END LOOP;
END;


#Query
DECLARE
  v_salary EMPLOYEES.Salary%TYPE;
  v_emp EMPLOYEES%ROWTYPE;
BEGIN
  SELECT Salary INTO v_salary FROM EMPLOYEES WHERE Employee_id = 101;
  DBMS_OUTPUT.PUT_LINE('Salary: ' || v_salary);

  SELECT * INTO v_emp FROM EMPLOYEES WHERE Employee_id = 101;
  DBMS_OUTPUT.PUT_LINE('Name: ' || v_emp.First_name || ' ' || v_emp.Last_name);
END;
