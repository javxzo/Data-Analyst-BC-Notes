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
`Select * FROM EmployeeDemographics
LEFT Outer Join EmployeeSalary
ON EmployeeDemographics.EmployeeID = EmployeeSalary.EmployeeID`
- Will result in everything from the left table and everything thats overlapping - but if its only in the right table then we do not want it.
> Left table is the first table used (EmployeeDemographics) and the right table is the second table used (EmployeeSalary).

### RIGHT OUTER JOIN
`Select * FROM EmployeeDemographics
RIGHT Outer Join EmployeeSalary
ON EmployeeDemographics.EmployeeID = EmployeeSalary.EmployeeID`
- Will result in everything from the right table and everything thats overlapping - but if its only in the left table then we do not want it.

### AMBIGUOUS COLUMN NAMES
`Select EmployeeID, FirstName, LastName, JobTitle, Salary
FROM EmployeeDemographics
Inner Join EmployeeSalary
ON EmployeeDemographics.EmployeeID = EmployeeSalary.EmployeeID`
- Will result in an ambiguous column name error 'EmployeeID'. 
- Need to clarify : EmployeeDemographics.EmployeeID. Due to the fact that we are using an inner join, using EmployeeSalary.EmployeeID results in the same thing. 
- If we were to use a 'Right outer join', we got all the information from our right table that doesnt have to be in our left table.
- If we were to use a 'Left outer join', we would see everything from our left table regardless if it was in our right table. 

## Unions
- Unions and joins are fairly similar, they are combining two tables to create one output. A join combines both tables based off of a common column. With a union, you are able to select all the data from both tables and put it into one output. 
- `SELECT * FROM EmployeeeDemographics FULL OUTER JOIN WarehouseEmployeeDemographics ON EmployeeDemographics.EmployeeID = WarehouseEmployeeDemographics.EmployeeID`
- Both of these tables have the same columns - employeeId, firstName, lastName...
`Select * FROM EmployeeDemographics UNION Select * FROM WarehouseEmployeeDemographics`
- This kind of union will remove the duplicates
- UNION ALL will show all the information regardless of it being a duplicate or not.

## Case
- A case statement allows you to specify a condition and specify what is returned when the condition is met.
- `SELECT FirstName, LastName, Age FROM EmployeeDemographics WHERE AGe is NOT NULL order by AGE`
- `SELECT FirstName, LastName, Age CASE WHEN Age > 30 then 'Old' ELSE 'Young' END FROM EmployeeDemographics WHERE AGe is NOT NULL order by AGE`
- a new column is created with the return value
- You can use multiple when values 
  ~~~ CASE 
        when age > 30 then 'OLD'
        when age between 27 and 30 then 'YOUNG'
        else 'baby'
    ~~~
    If there are multiple conditions that meet the criteria, it will return the first one that matches. 

## HAVING CLAUSE
~~~ Select Jobtitle, Count(Jobtitle)
    FROM EmployeeDemographics
    JOIN Employee Salary
    On EmployeeID
    Where Count(Jobtitle) > 1
Group by Jobtitle 
~~~
- This will result in an error, we cannot use this aggregate function in the where statement, we need to use a having clause.
~~~ Select Jobtitle, Count(Jobtitle)
    FROM EmployeeDemographics
    JOIN Employee Salary
    On EmployeeID
    Having Count(Jobtitle) > 1
Group by Jobtitle 
~~~
- This will still result in an error - this is due to the having statement being completely dependant on the group by statement because we are performing this after it has been aggregated. So the having statement needs to go AFTER the group by statement. 
~~~ Select Jobtitle, Count(Jobtitle)
    FROM EmployeeDemographics
    JOIN Employee Salary
    On EmployeeID    
Group by Jobtitle 
Having Count(Jobtitle) > 1
~~~

## Updating/Deleting Data

- `UPDATE TableName SET EmployeeID = 1012 WHERE FirstName = 'Holly' AND LastName = 'Flax'`
- `UPDATE TableName SET AGE = 31, Gender = 'Female' WHERE FirstName = 'Holly' AND LastName = 'Flax'`
- `DELETE FROM TableName WHERE EmployeeID = 1012`
- Trick is to turn it into a SELECT statement to check what you are erasing first.

## Aliasing column names
- Temporarily changing the column name in your script.
- Used for readability.
- `Select FirstName as Fname` or `Select FirstName fname` - both are viable options.
- `Select FirstName + ' ' + Lastname AS FullName`

## Aliasing table names
```SELECT Demo. EmployeeID, Sal.Salary
FROM [SQLTutorial]. [dbo]. [EmployeeDemographics] AS Demo
JOIN [SQLTutorial]. [dbo]. [EmployeeSalary] AS Sal
ON Demo. EmployeeID = Sal. EmployeeID
```

## Partition By
- Similar to group by
- The group by statement is different in the sense that it will reduce the number of rows in our output by rolling them up and then calculating the sums or averages for each group whereas partition by actually divides the result set into paritions and changes how the window(?) function is calculated. 
- So the partition by doesn't reduce the number of rows returned in our output. 
```SELECT FirstName, LastName, Gender, Salary
        , COUNT(Gender) OVER (PARTITION BY Gender) as TotalGender
        FROM SQLTutorial. .EmployeeDemographics dem
        JOIN SQLTutorial. .EmployeeSalary sal
        ON dem. EmployeeID = sal.EmployeeID
```
VERSUS
```
SELECT Gender, COUNT(Gender)
    FROM SQLTutorial. .EmployeeDemographics dem
    JOIN SQLTutorial. .EmployeeSalary sal
    ON dem.EmployeeID = sal.EmployeeID
    GROUP BY Gender
```
Allows you to see the information you couldn't with group by. FirstName, Lastname (...) is accessibile now with the column that has had an aggregate function performed on it.