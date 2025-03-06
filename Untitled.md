



SELECT name, psotition FROM Employees

SELECT name FROM Employees WHERE Salary >= 60000;

SELECT name, salary * 1.10 AS newSalary FROM Employees;

SELECT name FROM Employee WHERE name LIKE 'Sam ______ ';

ALTER TABLE Employee ADD 'Department' VARCHAR(50);