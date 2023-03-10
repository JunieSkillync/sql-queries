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
SELECT EmpId 
FROM EmployeeSalary 
WHERE Project IS NULL;
```
## 3. SQL query to fetch all the Employees from EmployeeDetails who joined in the Year 2020.

```sql
SELECT * FROM EmployeeDetails
WHERE DateOfJoining BETWEEN '2020/01/01'
AND '2020/12/31';
```
## 4. Fetch all employees from EmployeeDetails who have a salary record in EmployeeSalary.

```sql
SELECT * FROM EmployeeDetails E
WHERE EXISTS
(SELECT * FROM EmployeeSalary S 
WHERE  E.EmpId = S.EmpId);
```
## 5. Write an SQL query to fetch a project-wise count of employees sorted by project’s count in descending order.

```sql
SELECT Project, count(EmpId) EmpProjectCount
FROM EmployeeSalary
GROUP BY Project
ORDER BY EmpProjectCount DESC;
```
## 6.Fetch employee names and salaries even if the salary value is not present for the employee.

```sql
SELECT E.FullName, S.Salary 
FROM EmployeeDetails E 
LEFT JOIN 
EmployeeSalary S
ON E.EmpId = S.EmpId;
```
## 7.	Write an SQL query to fetch all the Employees who are also managers from the EmployeeDetails table..

```sql
SELECT DISTINCT E.FullName
FROM EmployeeDetails E
INNER JOIN EmployeeDetails M
ON E.EmpID = M.ManagerID;

```
## 8.	Write an SQL query to fetch duplicate records from EmployeeDetails.

```sql
SELECT FullName, ManagerId, DateOfJoining, City, COUNT(*)
FROM EmployeeDetails
GROUP BY FullName, ManagerId, DateOfJoining, City
HAVING COUNT(*) > 1;
```
## 9. Write an SQL query to fetch only odd rows from the table.

```sql
SELECT * FROM EmployeeDetails 
WHERE MOD (EmpId, 2) <> 0;
```
## 10.	Write a query to find the 3rd highest salary from a table without top or limit keyword.

```sql
SELECT Salary
FROM EmployeeSalary Emp1
WHERE 2 = (
                SELECT COUNT( DISTINCT ( Emp2.Salary ) )
                FROM EmployeeSalary Emp2
                WHERE Emp2.Salary > Emp1.Salary
            )
```
## 11.	Write an SQL query to fetch the EmpId and FullName of all the employees working under the Manager with id – ‘986’.

```sql
SELECT  EmpId, FullName
FROM EmployeeDetails
WHERE ManagerId = 986;
```
## 12.	Write an SQL query to fetch the different projects available from the EmployeeSalary table.

```sql
SELECT DISTINCT(Project)
FROM EmployeeSalary;
```
## 13.	Write an SQL query to fetch the count of employees working in project ‘P1’.

```sql
SELECT COUNT(*) 
FROM EmployeeSalary 
WHERE Project = 'P1';
```
## 14.	Write an SQL query to find the maximum, minimum, and average salary of the employees.

```sql
SELECT Max(Salary), 
Min(Salary), 
AVG(Salary) 
FROM EmployeeSalary;
```
## 15.	Write an SQL query to find the employee id whose salary lies in the range of 9000 and 15000.

```sql
SELECT EmpId, Salary
FROM EmployeeSalary
WHERE Salary BETWEEN 9000 AND 15000;

```
## 16.	Write an SQL query to fetch those employees who live in Toronto and work under the manager with ManagerId – 321.

```sql
SELECT EmpId, City, ManagerId
FROM EmployeeDetails
WHERE City='Toronto' AND ManagerId='321';
```
## 17.	Write an SQL query to fetch all the employees who either live in California or work under a manager with ManagerId – 321.

```sql
SELECT EmpId, City, ManagerId
FROM EmployeeDetails
WHERE City='California' OR ManagerId='321';
```
## 18.	Write an SQL query to fetch all those employees who work on Projects other than P1.

```sql
SELECT EmpId
FROM EmployeeSalary
WHERE NOT Project='P1';
```
## 19.	Write an SQL query to display the total salary of each employee adding the Salary with Variable value.

```sql
SELECT EmpId,
Salary+Variable as TotalSalary 
FROM EmployeeSalary;

```
## 20.	Write an SQL query to fetch the employees whose name begins with any two characters, followed by a text “hn” and ends with any sequence of characters.

```sql
SELECT FullName
FROM EmployeeDetails
WHERE FullName LIKE ‘__hn%’;
```
## 21.	Write an SQL query to fetch all the EmpIds which are present in either of the tables – ‘EmployeeDetails’ and ‘EmployeeSalary’.

```sql
SELECT EmpId FROM EmployeeDetails
UNION 
SELECT EmpId FROM EmployeeSalary;

```
## 22.	Write an SQL query to fetch common records between two tables. Ans. SQL Server – Using INTERSECT operator-

```sql
SELECT * FROM EmployeeSalary
INTERSECT
SELECT * FROM ManagerSalary;
```
## 23.	Write an SQL query to fetch records that are present in one table but not in another table. Ans. SQL Server – Using MINUS- operator-

```sql
SELECT * FROM EmployeeSalary
MINUS
SELECT * FROM ManagerSalary;
```
## 24.	Write an SQL query to fetch the EmpIds that are present in both the tables –  ‘EmployeeDetails’ and ‘EmployeeSalary.

```sql
SELECT EmpId FROM 
EmployeeDetails 
where EmpId IN 
(SELECT EmpId FROM EmployeeSalary);
```
## 25.	Write an SQL query to fetch the EmpIds that are present in EmployeeDetails but not in EmployeeSalary. Using subquery-

```sql
SELECT EmpId FROM 
EmployeeDetails 
where EmpId Not IN 
(SELECT EmpId FROM EmployeeSalary);
```
## 26.	Write an SQL query to fetch the employee’s full names and replace the space with ‘-’. Ans. Using the ‘Replace’ function-

```sql
SELECT REPLACE(FullName, ' ', '-') 
FROM EmployeeDetails;
```
## 27.	Write an SQL query to fetch the position of a given character(s) in a field. Ans. Using the ‘Instr’ function-

```sql
SELECT INSTR(FullName, 'Snow')
FROM EmployeeDetails;
```
## 28. Write an SQL query to display both the EmpId and ManagerId together.Ans. Here we can use the CONCAT command

```sql
SELECT CONCAT(EmpId, ManagerId) as NewId
FROM EmployeeDetails;
```
## 29.	Write a query to fetch only the first name(string before space) from the FullName column of the EmployeeDetails table. Ans. In this question, we are required to first fetch the location of the space character in the FullName field and then extract the first name out of the FullName field.

## For finding the location we will use the LOCATE method in MySQL and CHARINDEX in SQL SERVER and for fetching the string before space, we will use the SUBSTRING OR MID method.

## MySQL – using MID

```sql
SELECT MID(FullName, 1, LOCATE(' ',FullName)) 
FROM EmployeeDetails;
```
## 30.	Write an SQL query to uppercase the name of the employee and lowercase the city values.

```sql
SELECT UPPER(FullName), LOWER(City) 
FROM EmployeeDetails;
```

## 31.	Write an SQL query to find the count of the total occurrences of a particular character – ‘n’ in the FullName field.

```sql
SELECT FullName, 
LENGTH(FullName) - LENGTH(REPLACE(FullName, 'n', ''))
FROM EmployeeDetails;
```

## 32.	Write an SQL query to find the current date-time.

```sql
SELECT NOW();
```

## 33.	Write an SQL query to fetch all the Employee details from the EmployeeDetails table who joined in the Year 2020.

```sql
SELECT * FROM EmployeeDetails
WHERE DateOfJoining BETWEEN '2020/01/01'
AND '2020/12/31';
```

## 34.	Write an SQL query to fetch all employee records from the EmployeeDetails table who have a salary record in the EmployeeSalary table.

```sql
SELECT * FROM EmployeeDetails E
WHERE EXISTS
(SELECT * FROM EmployeeSalary S 
WHERE  E.EmpId = S.EmpId);
```

## 35.	Write an SQL query to fetch the project-wise count of employees sorted by project’s count in descending order.

```sql
SELECT Project, count(EmpId) EmpProjectCount
FROM EmployeeSalary
GROUP BY Project
ORDER BY EmpProjectCount DESC;
```

## 36.	Write a query to fetch employee names and salary records. Display the employee details even if the salary record is not present for the employee.

```sql
SELECT E.FullName, S.Salary 
FROM EmployeeDetails E 
LEFT JOIN 
EmployeeSalary S
ON E.EmpId = S.EmpId;
```

## 37.	Write an SQL query to fetch all the Employees who are also managers from the EmployeeDetails table.

```sql
SELECT DISTINCT E.FullName
FROM EmployeeDetails E
INNER JOIN EmployeeDetails M
ON E.EmpID = M.ManagerID;
```
## 38.	Write an SQL query to fetch duplicate records from EmployeeDetails (without considering the primary key – EmpId).

```sql
SELECT FullName, ManagerId, DateOfJoining, City, COUNT(*)
FROM EmployeeDetails
GROUP BY FullName, ManagerId, DateOfJoining, City
HAVING COUNT(*) > 1;
```
## 39.	Write an SQL query to remove duplicates from a table without using a temporary table.

```sql
DELETE E1 FROM EmployeeDetails E1
INNER JOIN EmployeeDetails E2 
WHERE E1.EmpId > E2.EmpId 
AND E1.FullName = E2.FullName 
AND E1.ManagerId = E2.ManagerId
AND E1.DateOfJoining = E2.DateOfJoining
AND E1.City = E2.City;
```

## 40.	Write an SQL query to fetch only odd rows from the table.

```sql
SELECT * FROM EmployeeDetails 
WHERE MOD (EmpId, 2) <> 0;
```

## 41.	Write an SQL query to create a new table with data and structure copied from another table.

```sql
CREATE TABLE NewTable 
SELECT * FROM EmployeeSalary;
```

## 42.	Write an SQL query to create an empty table with the same structure as some other table.

```sql
CREATE TABLE NewTable 
SELECT * FROM EmployeeSalary where 1=0;
```

## 43.	Write an SQL query to find the nth highest salary from a table.

```sql
SELECT Salary
FROM Employee
ORDER BY Salary DESC LIMIT N-1,1;
```

## 44.	Write SQL query to find the 3rd highest salary from a table 

```sql
SELECT Salary
FROM EmployeeSalary Emp1
WHERE 2 = (
            SELECT COUNT( DISTINCT ( Emp2.Salary ) )
            FROM EmployeeSalary Emp2
            WHERE Emp2.Salary > Emp1.Salary
            )
```

![bg width:1000px](./Patients.png)

![bg width:1000px](./PatientsCheckup.png)

## 45.	Write a SQL query to fetch the PatientName in uppercase and state as lowercase. Also use the ALIAS name for the result-set as PatName and NewState.

```sql

```

## 46.	Find the Nth highest consultation fees from the PatientsCheckup table.

```sql

```

## 47.	Write a query to fetch top N records ordered by ConsultationFees.

```sql

```

## 48.	Write a query to retrieve the list of patients from the same state.

```sql

```

## 49.	Write a query to retrieve two minimum and maximum consultation fees from the PatientsCheckup Table.

```sql

```

## 50.	Write a query to fetch patient details along with the weight fees, even if the details are missing.

```sql

```

## 51.	Write a SQL query to fetch doctor wise count of patients sorted by the doctors

```sql

```
## 52.	Write a SQL query to fetch the first and last record of the Patients table.

```sql

```

## 53.	Write a SQL query to fetch consultation fees – wise count and sort them in descending order.

```sql

```

## 54.	Write a SQL query to retrieve patient details from the Patients table who have a weight in the PatientsCheckup table.

```sql

```

## 55.	Write a SQL query to retrieve the last 2 records from the Patients table.

```sql

```

