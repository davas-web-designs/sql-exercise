### Aggregate functions and group by

1. Write a query to list the number of jobs available in the employees table.

   *Solution:*
   
   ```
   select count(distinct job_id) from employees;
   ```
   
2. Write a query to get the total salaries payable to employees.

   Note: sum all the salaries

   *Solution:*
   
   ```
   select sum(salary) from employees;
   ```
   
3. Write a query to get the minimum salary from employees table.

  *Solution:*
  
  ```
  select min(salary) from employee;
  ```
  
4. Write a query to get the maximum salary of an employee working as a Programmer.

   *Solution:*
   
   ```
   select max(salary) from employees where job_id = "IT_PROG";
   ```
   
5. Write a query to get the average salary and number of employees working the department 90.

   *Solution:*
   
   ```
   select avg(salary), count(*) from employees where department_id = "90";
   ```
   
6. Write a query to get the highest, lowest, sum, and average salary of all employees.

   *Solution:*
   ```
   select max(salary), min(salary), sum(salary), avg(salary) from employees;
   ```
   
7. Write a query to get the number of employees with the same job.

   *Solution:*
   
   ```
   select job_id ,count(*) from employees group by job_id;
   ```
   
8. Write a query to get the difference between the highest and lowest salaries.

   *Solution*

   ```
   select max(salary)-min(salary) from employees;   
   ```
   
9. Write a query to find the manager ID and the salary of the lowest-paid employee for that manager.
   
   *Solution*
   
   ```
   select manager_id, min(salary) from employees where manager_id is not null group by manager_id order by min(salary) desc;
   ```
   
10. Write a query to get the department ID and the total salary payable in each department.

    *Solution*
    
    ```
    select department_id , sum(salary) from employees group by department_id;
    ```
    
11. Write a query to get the average salary for each job ID excluding programmer.  

    *Solution*
    
    ```
    select avg(salary) from employees where job_id <> "IT_PROG" group by job_id;
    ```
    
12. Write a query to get the total salary, maximum, minimum, average salary of employees (job ID wise), for department ID 90 only    
    
    *Solution*
    
    ```
    select job_id, sum(salary), max(salary), min(salary), avg(salary) from employees where department_id = 90 group by job_id;
    ```
    
13. Write a query to get the job ID and maximum salary of the employees where maximum salary is greater than or equal to $4000.

    *Solution:*
    
    ```
    select job_id , max(salary) from employees group by job_id having max(salary) >= 4000;
    ```
    
14. Write a query to get the average salary for all departments employing more than 10 employees.

    *Solution:*
    
    ```
    select avg(salary) from employees group by department_id having count(*) > 10;
    ```
    
    





   
