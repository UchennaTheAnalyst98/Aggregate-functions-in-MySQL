#   GROUPING A TABLE USING THE GROUP BY FUNCTION;

USE deff;

SELECT *
FROM employees;

# LETS UPDATE OUR TABLE FIRSTLY;
UPDATE employees
SET email =  'uche@deff.com', 
			        salary = 45000
WHERE employee_id = 1;

UPDATE employees
SET email =    'gideon@deff.com', 
			          salary = 38000
WHERE employee_id = 2;

UPDATE employees
SET email =  'sarah@deff.com', 
			        salary = 48000
WHERE employee_id = 3;

UPDATE employees
SET email =  'onyi@deff.com', 
			        salary = 39000
WHERE employee_id = 4;

SELECT *
FROM employees;

# TOTAL AMOUNT EARNED BY MALE AND FEMALE;

SELECT gender, 
	SUM(salary) AS total_salary
FROM employees
GROUP BY gender;

#AVERAGE SALARY FOR EACH GENDER

SELECT gender, 
	AVG(salary) AS Average_salary
FROM employees
GROUP BY gender;

# TO ROUND THE ABOVE OUTCOME

SELECT gender,  
	CEIL(AVG(salary)) AS Average_salary
FROM employees
GROUP BY gender;

# TO FILTER THE ABOVE OUTCOME;
SELECT gender, 
	CEIL(AVG(salary)) AS Average_salary
FROM employees
GROUP BY gender
HAVING Average_salary > 43000;


# USING THE WHERE CLAUSE BUT NOT IN THE AGGREGATED FUNCTION
SELECT gender, 
	CEIL(AVG(salary)) AS Average_salary
FROM employees
WHERE gender = 'male'
GROUP BY gender;
