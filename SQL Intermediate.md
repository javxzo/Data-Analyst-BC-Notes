# SQL - Intermediate 

## Joins
![Join-Visual](joins.png)
### INNER JOINS
- A join is a way to combine multiple tables into a single output. 
> EmployeeDemographic - EmployeeID, FirstName, LastName, Age, Gender

> EmployeeSalary - EmployeeID, JobTitle, Salary

- Joins are created off of similar columns - in this case, we are going to look at employeeID.
`Select * FROM EmployeeDemographics
Inner Join EmployeeSalary
ON EmployeeDemographics.EmployeeID = EmployeeSalary.EmployeeID`
- This code outputs all of the columns from both tables and shows everything that is the same.


### FULL OUTER JOIN
`Select * FROM EmployeeDemographics
Full Outer Join EmployeeSalary
ON EmployeeDemographics.EmployeeID = EmployeeSalary.EmployeeID`
- This results in a different graph - if there is an employeeID of 1013 on the EmployeeDemographics data but not on the EmployeeSalary data, it will fill the respective values with null (and vice versa)
- It includes all values - regardless if the rest of the row is filled out.

### LEFT OUTER JOIN

