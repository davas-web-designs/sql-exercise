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

   
