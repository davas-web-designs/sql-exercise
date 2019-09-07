### subqueries

1. Write a query to find the name (first_name, last_name) and the salary of the employees who have a higher salary than the employee whose last_name='Bull'.

   *Solution:*
   
   ```
   select first_name, last_name from employees where salary > (Select salary from employees where last_name = "Bull");
   ```
   
2. Write a query to find the name (first_name, last_name) of all employees who works in the IT department.
   
   Note: uses both employees and departments tables
   
   *Solution:*
   
   ```
   select first_name, last_name from employees where department_id in (select department_id from departments where department_name = "IT");
   ```
   
3. Write a query to find the name (first_name, last_name) of the employees who have a manager and worked in a USA based department.

   Hint : Write single-row and multiple-row subqueries. Use departments, employees, locations table.
   
   *Solution:*
   
   ```
   SELECT first_name, last_name FROM employees 
   WHERE manager_id in (select employee_id 
   FROM employees WHERE department_id 
   IN (SELECT department_id FROM departments WHERE location_id 
   IN (select location_id from locations where country_id='US')));
   ```
   
4. Write a query to find the name (first_name, last_name) of the employees who are managers.   
   
   *Solution:*
   
   ```
   select first_name, last_name from employees where employee_id in (select manager_id from departments);
   ```

5. Write a query to find the name (first_name, last_name), and salary of the employees whose salary is greater than the average salary.

   *Solution:*
   
   ```
   select first_name, last_name,salary from employees where salary > (select avg(salary) from employees);
   ```
   
6. Write a query to find the name (first_name, last_name), and salary of the employees whose salary is equal to the minimum salary for their job grade.   
   
   Note: use various tables...
   
   *Solution:*
   
   ```
   select first_name, last_name, salary from employees where employees.salary = (select min_salary from jobs where employees.job_id = jobs.job_id);
   ```
   
7. Write a query to find the name (first_name, last_name), and salary of the employees who earns more than the average salary and works in any of the IT departments.

   *Solution:*
   
   ```
   select first_name, last_name, salary 
   from employees
   where department_id in (select department_id from department where department_name like "%IT%")
   and salary > (select avg(salary) from employees);
   ```
   
8. Write a query to find the name (first_name, last_name), and salary of the employees who earns more than the earning of Mr. Bell. 
   
   *Solution:*
   
   ```
   select first_name, last_name, salary
   from employees
   where salary > (select salary from employees where last_name = "Bell");
   ```
   
9. Write a query to find the name (first_name, last_name), and salary of the employees who earn the same salary as the minimum salary for all departments.
   
   *Solution:*
   
   ```
   select first_name, last_name, salary
   from employees
   where salary = (select min(salary) from employees);
   ```
   
10. Write a query to find the name (first_name, last_name), and salary of the employees whose salary is greater than the average salary of all departments.

   *Solution:*
   
   ```
   select first_name, last_name, salary from employees where salary > all(select avg(salary) from employees group by department_id);
   ```
   
11. Write a query to find the name (first_name, last_name) and salary of the employees who earn a salary that is higher than the salary of all the Shipping Clerk (JOB_ID = 'SH_CLERK'). Sort the results of the salary of the lowest to highest.

    *Solution:*
    
    ```
    select first_name, last_name, salary from employees where salary > all(select salary from employees where job_id = "SH_CLERCK") order by salary;
    ```
    
12. Write a query to find the name (first_name, last_name) of the employees who are not supervisors.    

    *Solution:*
    
    ```
    select b.first_name, b.last_name from employees b where not exists (select "X" from employees a where a.manager_id = b.employee_id);
    ```
    
13. Write a query to display the employee ID, first name, last name, and department names of all employees.

    *Solution:*
    
    ```
    select a.employee_id, a.first_name, a.last_name, b.department_name from employees as a, departments as b where a.department_id = b.department_id;
    ```
    
14. Write a query to display the employee ID, first name, last name, salary of all employees whose salary is above average for their departments.

    *Solution:*
    
    ```
    select a.employee_id, a.first_name, a.last_name from employees as a where a.salary > (select avg(salary) from employees as e where a.department_id = e.department_id);
    ```
    
15. Write a query to fetch even numbered records from employees table.

    Note: this may not work depending on mysql version.

    *Solution:*
    
    ```
    SET @i = 0; 
    SELECT i, employee_id 
    FROM (SELECT @i := @i + 1 AS i, employee_id FROM employees)
    a WHERE MOD(a.i, 2) = 0;
    ```

16. Write a query to find the 5th maximum salary in the employees table.

    *Solution:*
    
    ```
    select distinct salary from employees as e1 where 5 = (select count(distinct e2.salary) from employees as e2 where e2.salary >= e1.salary);
    ```
    
17. Write a query to find the 4th minimum salary in the employees table.

    *solution:*
    
    ```
    select distinct salary from employees as e1 where 4 = (select count(distinct e2.salary) from employees as e2 where e2.salary <= e1.salary);
    ```
    
18. Write a query to select last 10 records from a table.

    *Solution:*
    
    ```
    SELECT * FROM (
    SELECT * FROM employees ORDER BY employee_id DESC LIMIT 10) sub 
    ORDER BY employee_id ASC;
    ```
    
20. Write a query to get 3 maximum salaries.

    *Solution:*
    
    ```
    select salary from employees order by salary desc limit 3;
    ```
    
21. Write a query to get 3 minimum salaries.

    *Solution:*
    
    ```
    select distinct salary from employees order by salary asc limit 3;
    ```
    
22. Write a query to get nth max salaries of employees.

    *Solution:*
    
    
   
   
   
   
   
   
