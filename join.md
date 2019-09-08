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

   
