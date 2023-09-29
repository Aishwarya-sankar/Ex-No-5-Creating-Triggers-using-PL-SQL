# Ex-No-5-Creating-Triggers-using-PL-SQL
AIM: To create a Trigger using PL/SQL.
Steps:
Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
Create a trigger named as log_salary-update.
Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
End the trigger.
Update the salary of an employee in employee table.
Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
Display the employee table, salary_log table.
Program:
CREATE TABLE employed(
  empid NUMBER,
  empname VARCHAR2(10),
  dept VARCHAR2(10),
  salary NUMBER
);

CREATE TABLE sal_log (
  log_id NUMBER GENERATED ALWAYS AS IDENTITY,
  empid NUMBER,
  empname VARCHAR2(10),
  old_salary NUMBER,
  new_salary NUMBER,
  update_date DATE
);
Create employee table
270856486-efa5fa81-9159-4454-952c-ac97d4c8e202

Create salary_log table
270856619-afcec037-26b9-4bc4-8847-2c98c307a6e9

PLSQL Trigger code
->Create the trigger
Create the trigger
CREATE OR REPLACE TRIGGER log_sal_update
BEFORE UPDATE ON employed
FOR EACH ROW
BEGIN
  IF :OLD.salary != :NEW.salary THEN
    INSERT INTO sal_log (empid, empname, old_salary, new_salary, update_date)
    VALUES (:OLD.empid, :OLD.empname, :OLD.salary, :NEW.salary, SYSDATE);
  END IF;
END;
/
->Update the salary of an employee
UPDATE employed
SET salary = 60000
WHERE empid = 1;
->Display the employee table
SELECT * FROM employed;

->Display the salary_log table
SELECT * FROM sal_log;
Output:
270856824-52c0e45c-ace8-4660-9850-473976410fce

Result:
The program has been implemented successfully.