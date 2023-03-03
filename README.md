# sql-queries

![bg width:1000px](./Screenshot_1.png)

## 1. SQL Query to fetch records from that are present in one table but not in another table.

```sql
SELECT EmployeeDetails.*
FROM EmployeeSalary
LEFT JOIN
EmployeeSalary USING (EmpId)
WHERE EmployeeSalary.EmpId IS NULL;
```