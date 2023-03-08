# sql-queries

![bg width:1000px](./Screenshot_1.png)

![bg width:1000px](./EmployeeSalary.png)
## 1. SQL Query to fetch records from that are present in one table but not in another table.

```sql
SELECT EmployeeDetails.*
FROM EmployeeSalary
LEFT JOIN
EmployeeSalary USING (EmpId)
WHERE EmployeeSalary.EmpId IS NULL;
```
## 2. SQL query to fetch all the employees who are not working on any project.

```sql
SELECT DISTINCT(Project)
FROM EmployeeSalary;
```
## 3. SQL query to fetch all the Employees from EmployeeDetails who joined in the Year 2020.

```sql
SELECT COUNT(*) 
FROM EmployeeSalary 
WHERE Project = 'P1';
```
## 4. Fetch all employees from EmployeeDetails who have a salary record in EmployeeSalary.

```sql
SELECT Max(Salary), 
Min(Salary), 
AVG(Salary) 
FROM EmployeeSalary;
```
## 5. Write an SQL query to fetch a project-wise count of employees.

```sql

```
## 6.Fetch employee names and salaries even if the salary value is not present for the employee.

```sql

```
## 7.	Write an SQL query to fetch all the Employees who are also managers.

```sql

```
## 8.	Write an SQL query to fetch duplicate records from EmployeeDetails.

```sql

```
## 9. Write an SQL query to fetch only odd rows from the table.

```sql

```
## 10.	Write a query to find the 3rd highest salary from a table without top or limit keyword.

```sql

```
## 11.	Write an SQL query to fetch the EmpId and FullName of all the employees working under the Manager with id – ‘986’.

```sql

```
## 12.	Write an SQL query to fetch the different projects available from the EmployeeSalary table.

```sql

```
## 13.	Write an SQL query to fetch the count of employees working in project ‘P1’.

```sql

```
## 14.	Write an SQL query to find the maximum, minimum, and average salary of the employees.

```sql

```
## 15.	Write an SQL query to find the employee id whose salary lies in the range of 9000 and 15000.

```sql

```
## 16.	Write an SQL query to fetch those employees who live in Toronto and work under the manager with ManagerId – 321.

```sql

```
## 17.	Write an SQL query to fetch all the employees who either live in California or work under a manager with ManagerId – 321.

```sql

```
## 18.	Write an SQL query to fetch all those employees who work on Projects other than P1.

```sql

```
## 19.	Write an SQL query to display the total salary of each employee adding the Salary with Variable value.

```sql

```
## 20.	Write an SQL query to fetch the employees whose name begins with any two characters, followed by a text “hn” and ends with any sequence of characters.

```sql

```
## 21.	Write an SQL query to fetch all the EmpIds which are present in either of the tables – ‘EmployeeDetails’ and ‘EmployeeSalary’.

```sql

```
## 22.	Write an SQL query to fetch common records between two tables. Ans. SQL Server – Using INTERSECT operator-

```sql

```
## 23.	Write an SQL query to fetch records that are present in one table but not in another table. Ans. SQL Server – Using MINUS- operator-

```sql

```
## 24.	Write an SQL query to fetch the EmpIds that are present in both the tables –  ‘EmployeeDetails’ and ‘EmployeeSalary.

```sql

```
## 25.	Write an SQL query to fetch the EmpIds that are present in EmployeeDetails but not in EmployeeSalary. Using subquery-

```sql

```
## 26.	Write an SQL query to fetch the employee’s full names and replace the space with ‘-’. Ans. Using the ‘Replace’ function-

```sql

```
## 27.	Write an SQL query to fetch the position of a given character(s) in a field. Ans. Using the ‘Instr’ function-

```sql

```
## 28. Write an SQL query to display both the EmpId and ManagerId together.Ans. Here we can use the CONCAT command

```sql

```
## 29.	Write a query to fetch only the first name(string before space) from the FullName column of the EmployeeDetails table. Ans. In this question, we are required to first fetch the location of the space character in the FullName field and then extract the first name out of the FullName field.

## For finding the location we will use the LOCATE method in MySQL and CHARINDEX in SQL SERVER and for fetching the string before space, we will use the SUBSTRING OR MID method.

## MySQL – using MID

```sql

```



