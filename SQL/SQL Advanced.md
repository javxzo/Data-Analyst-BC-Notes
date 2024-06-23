# Advanced SQL Tutorial

- CTE
- Temp Tables
- String Functions
- Stored Procedures
- Subqueries

### CTEs - Common Table Expression
- it's a named temporary result set which is used to manipulate the complex subquery's data.
- This only exists in the scope of the statement that we are about to write. Once we cancel out of this query, it's like it never existed.
- Only created in memory rather than a tempdb file like a temp table would be. 
- Sometimes called with queries

* Query
~~~
WITH CTE_Employee as (
    SELECT FirstName, LastName, Gender, Salary, 
    COUNT(gender) OVER (PARTITION by Gender) as TotalGender, 
    AVG(Salary) OVER (PARTITION BY Gender) as AvgSalary
    FROM SQLTutorial..EmployeeDemographics emp
    JOIN SQLTutorial..EmployeeSalary sal
    ON emp.EmployeeID = sal.EmployeeID
    WHERE Salary > '45000'
)
~~~
This is putting it in a temporary place where we can then go and grab that data. 
`Select * FROM CTE_Employee`
- Will show everything from the fake table - acts more like a subquery
- Due to the CTE_Employee table only being stored in memory, we cannot run `Select * FROM CTE_Employee` by itself. It needs to be ran with the previous * query everytime. 
- You also MUST put the SELECT statement right underneath the CTE query. 

### Temp Tables
~~~
CREATE TABLE #temp_Employee (
    EmployeeID int, 
    JobTitle varchar(100)
    Salary int
)
INSERT INTO #temp_Employee VALUES (
    '1001', 'HR', '45000'
)
SELECT * FROM #temp_Employer
~~~

- Rather than inserting like in the previous query, we can also take all the data from a specific table and insert that into a temp table.

~~~
INSERT INTO #temp_Employee
SELECT *
FROM Employee..Salary
~~~

This is one of the big uses of a temp table. If the salary table had a million rows, and we were trying to complete a complex query off of it where we're using joins and other things, it would take a long time. We could create a subtable that only has the information that we want to use and cut down the time it takes. 
- Add DROP TABLE IF EXISTS #Temp_Employee2

### String Functions
- TRIM, LTRIM, RTRIM, REPLACE, SUBSTRING, UPPER, LOWER

~~~
CREATE TABLE EmployeeErrors (
    EmployeeID varchar(50),
    FirstName varchar(50),
    LastName varchar(50)
)

Insert into EmployeeErrors Values
    ('1001 ', 'Jimbo', 'Halbert'),
    (' 1002', 'Pamela', 'Beasely'),
    ('1005', 'TOby', 'Flenderson - Fired')

SELECT * FROM EmployeeErrors

SELECT EmployeeID, TRIM(EmployeeID) as IDTRIM
FROM EmployeeErrors
SELECT EmployeeID, RTRIM(EmployeeID) as IDTRIM
FROM EmployeeErrors
SELECT EmployeeID, LTRIM(EmployeeID) as IDTRIM
FROM EmployeeErrors

SELECT LastName, Replace(LastName, '- Fired', '') as LastNameFixed
FROM EmployeeErrors

SELECT SUBSTRING(FirstName, 1, 3) // going to start at the very first stop and go forward three values
FROM EmployeeErrors
~~~

Fuzzy Matching - Alex and Alexander (won't match if you try to join)

~~~
SELECT *
    FROM EmployeeErrors err
    Join EmployeeDemographics dem
        ON SUBSTRING(err.FristName, 1, 3) = SUBSTRING(dem.FirstName, 1, 3)
~~~
- Would need to verify with Gender, Lastname, DOB etc.

~~~
SELECT FristName, Lower(FirstName)
FROM EmployeeErrors
SELECT FristName, Upper(FirstName)
FROM EmployeeErrors
~~~

### Stored Procedures
- A stored procedure is a group of SQL statements that has been created and stored in that db. A stored procedure can accept input parameters.
- Similar to a method.

~~~
CREATE PROCEDURE TEST
AS
(Input Query) SELECT * FROM EmployeeDemographics
~~~
To Run: `EXEC TEST`

- You can go into the procedure file to alter it 
- Below `Alter Procedure` you can add parameters like `@JobTitle nvarchar(100)`
- And then use `WHERE JobTitle = @JobTitle`

~~~
EXEC Temp_Employee @JobTitle = 'Salesman'
~~~

### Subqueries
In Select
~~~
SELECT EmployeeID, Salary (SELECT (AVG(Salary) FROM EmployeeSalary AS AllAvgSalary))
FROM EmployeeSalary
~~~
In Partition By
```
SELECT EmployeeID, Salary (AVG(Salary) over () as AllavgSalary)
FROM EmployeeSalary
```
Why Group By doesn't work
~~~
SELECT EmployeeID, Salary, AVG(Salary) as AllavgSalary
FROM EmployeeSalary
Group By EmployeeId, Salary
Order By 1,2
~~~
Subquery in FROM
~~~
SELECT *
FROM (SELECT EmployeeID, Salary (AVG(Salary) over () as AllavgSalary) FROM EmployeeSalary)
~~~
Subquery in Where
~~~
SELECT EmployeeID, JobTitle, Salary
FROM EmployeeSalary
WHERE EmployeeID in (Select * FROM EmployeeDemographics)
~~~

