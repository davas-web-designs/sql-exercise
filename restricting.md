### Restricting and sorting data

1. Write a query to display the name (first_name, last_name) and salary for all employees whose salary is not in the range $10,000 through $15,000.
   
   *Solution:*
   
   ```
   select first_name, last_name, salary from employees where salary not between 10000 and 15000;
   ```

2. Write a query to display the name (first_name, last_name) and department ID of all employees in departments 30 or 100 in ascending order.

   *Solution:*
   
   ```
   select first_name, last_name , salary from employees where department_id in (30,100) order by department_id asc;
   ```

3. Write a query to display the name (first_name, last_name) and salary for all employees whose salary is not in the range $10,000 through $15,000 and are in department 30 or 100.

   *Solution:*
   
   ```
   select first_name, last_name , salary from employees where salary not between 10000 and 15000 and department_id in (30,100);
   ```

4. Write a query to display the name (first_name, last_name) and hire date for all employees who were hired in 1987.

   *Solution:*
   
   ```
   select first_name , last_name, hire_date from employees where year(hire_date) like '1987%';
   ```
 
5. Write a query to display the first_name of all employees who have both "b" and "c" in their first name.

   *Solution:*
   
   ```
   select first_name from employees where first_name like "%b%" and first_name like "%c%";
   ```
     
6. Write a query to display the last name, job, and salary for all employees whose job is that of a Programmer or a Shipping Clerk, and whose salary is not equal to $4,500, $10,000, or $15,000.
  
   *Solution:*
   
   ```
   select last_name, job_id, salary from employees where job_id in ("IT_PROG", "ST_CLERK") and salary not in (4500, 10000, 15000);
   ```

7. Write a query to display the last name of employees whose names have exactly 6 characters.

   *Solution:*
   
   ```
   select last_name from employees where last_name like "______";
   ```
   
8. Write a query to display the last name of employees having 'e' as the third character.

   *Solution:*
   
   ```
   select last_name from employees where last_name like "__e%";
   ```
 
9. Write a query to display the jobs/designations available in the employees table.

   *Solution:*
   
   ```
   select distinct job_id from employees;
   ```
 
10. Write a query to display the name (first_name, last_name), salary and PF (15% of salary) of all employees.

    *Solution:*
    
    ```
    select first_name, last_name, salary, salary * .15 "PF" from employees;
    ```
    
11. Write a query to select all record from employees where last name in 'BLAKE', 'SCOTT', 'KING' and 'FORD'.

    *Solution:*
    
    ```
    select * from employees where last_name in ("BLAKE", "SCOTT", "KING", "FORD");
    ```
   
   
