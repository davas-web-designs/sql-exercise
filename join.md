### joins

1. Write a query to find the addresses (location_id, street_address, city, state_province, country_name) of all the departments.
   
   HINT: use NATURAL JOIN
   
   *Solution:*
   
   ```
   select location_id, street_address, city, state_province, country_name from locations natural join countries;
   ```
   
2. Write a query to find the name (first_name, last name), department ID and name of all the employees.

   *solution:*
   
   ```
   select first_name, last_name, department_id, department_id from employees join departments using (department_id);
   ```
   
3. Write a query to find the name (first_name, last_name), job, department ID and name of the employees who works in London.
   
   *Solution:*
   
   ```
   select first_name, last_name, job_id, department_id, department_name from employees join departments using (department_id) join locations using (location_id) where city = "LONDON";
   ```
   
4. Write a query to find the employee id, name (last_name) along with their manager_id and name (last_name).

   *Solution:*
   
   ```
   select e.employee_id , e.last_name, e.manager_id, m.last_name from employees e join employees m on (e.manager_id = m.employee_id);
   ```
   
5. Write a query to find the name (first_name, last_name) and hire date of the employees who was hired after 'Jones'.

   *Solution:*
   
   ```
   select first_name, last_name, hire_date from employees where hire_date > (select hire_date from employees where las_name = "Jones");
   ```
   ```
   SELECT e.first_name, e.last_name, e.hire_date 
   FROM employees e 
   JOIN employees davies 
   ON (davies.last_name = 'Jones') 
   WHERE davies.hire_date < e.hire_date;
   ```
   
6. Write a query to get the department name and number of employees in the department.

   *Solution:*
   
   ```
   select count(*), department_name from employees e join departments d on (e.department_id = d.department_id) group by e.department_id;
   ```

7. Write a query to find the employee ID, job title, number of days between ending date and starting date for all jobs in department 90.

   *Solution:*
   
   ```
   select employee_id, job_id, end_date - start_date 
   from job_history
   natural join jobs
   where department_id = 90;
   ```
   
8. Write a query to display the department ID and name and first name of manager.

   *Solution:*
   
   ```
   select d.department_id, d.first_name , d.last_name 
   from departments as d
   inner join employees e 
   on (d.manager_id = e.employee_id);
   ```
   
9. Write a query to display the department name, manager name, and city.

   *Solution:*
   
   ```
   select d.department_name, e.first_name, e.last_name, l.city
   from employees as e
   inner join departments as d on (e.employee_id = d.manager_id)
   inner join locations as l on (d.location_id = l.location_id);
   ```
   
10. Write a query to display the job title and average salary of employees

    *Solution:*
    
    ```
    select job_title, avg(salary)
    from employees 
    join jobs
    using (job_id)
    group by job_id;
    ```
    
11. Write a query to display job title, employee name, and the difference between salary of the employee and minimum salary for the job.

   *Solution:*
   
   ```
   select job_title, e1.first_name, e1.last_name, e1.salary - (select min(salary) from employees as e2 where e2.job_id = e1.job_id)
   from employees as e1
   join jobs as j
   on (e1.job_id = j.job_id); 
   ```
   ```
   select job_title, first_name, last_name, salary - min_salary
   from employees
   natural join jobs;
   ```
   
12. Write a query to display the job history that were done by any employee who is currently drawing more than 10000 of salary.

    *Solution:*
    
    ```
    ```


   



