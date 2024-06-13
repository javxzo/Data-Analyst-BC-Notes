# The Basics - SQL!
Using [SQl Server Management Studio (SMSS)](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver15) and [SQL Server Express](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)

> New Database > SQLTutorial

### Creating Tables
- Two ways to do this
  - New > Table
  - Script:
    `CREATE TABLE NameOfTable (NameOfVar, VarType...)`

~~~
CREATE TABLE EmployeeDemographics
    (EmployeeID int,
    FirstName varChar(50),
    LastName varChar(50),
    Age int,
    Gender varchar(50)
    )
CREATE TABLE EmployeeSalary
    (EmployeeID int,
    JobTitle varChar(50),
    Salary int) 
~~~   

CTRL+K, CRTL+C to comment out on SSMS

### INSERT into table
~~~
Insert into EmployeeDemographics VALUES
(1001, 'Jim', 'Halpert', 30, 'Male'),
(1002, 'Pam', 'Beasley', 30, 'Female'),
(1003, 'Dwight', 'Schrute', 29, 'Male'),
(1004, 'Angela', 'Martin', 31, 'Female'),
(1005, 'Toby', 'Flenderson', 32, 'Male'),
(1006, 'Michael', 'Scott', 35, 'Male'),
(1007, 'Meredith', 'Palmer', 32, 'Female'),
(1008, 'Stanley', 'Hudson', 38, 'Male'),
(1009, 'Kevin', 'Malone', 31, 'Male')

INSERT INTO EmployeeSalary VALUES
(1001, 'Salesman', 45000),
(1002, 'Receptionist', 36000),
(1003, 'Salesman', 63000),
(1004, 'Accountant', 47000),
(1005, 'HR', 50000),
(1006, 'Regional Manager', 65000),
(1007, 'Supplier Relations', 41000),
(1008, 'Salesman', 48000),
(1009, 'Accountant', 42000)
~~~

### SELECT & FROM Statements

`SELECT * FROM EmployeeSalary` - Gives you all the values in EmployeeSalary
`SELECT FirstName, LastName FROM EmployeeDemographics` - Gives you (ONLY) first and last names from that table. 
`SELECT TOP 5 * from EmployeeDemographics` - Gives you the top 5 rows for all columns.

### DISTINCT KEYWORD
`SELECT DISTINCT(EmployeeID) FROM EmpDemo` will give you all the current values because we know there are not repeats. While `Distinct(Gender)` will only result in 2.

### COUNT 
`SELECT Count(LastName) FROM EmpDemo` 
will return all **NON-NULL** last names. 
This is derived information so there is no column name

`SELECT Count(LastName) AS LastNameCount FROM EmpDemo` will result with the column name being labelled. 

### MAX
`SELECT MAX(Salary) FROM empSalary` will return the largest value.
- `AVG` returns the average value and `MIN` returns the minimum value. 

### Switching Databases
- in the case where you are working on a seperate database and want to access another, we can do as following:
`SELECT * FROM SQLTutorial.dbo.EmployeeSalary`

### WHERE
`SELECT * FROM EmpDemo WHERE Age > 30` will show all individuals over the age of 30.
We can change it to `WHERE Age <= 32 AND Gender = 'Male'` OR `WHERE Age <= 32 OR Gender = 'Male'`.

### LIKE
Let's say you want everybody whose last name starts with S. 
`SELECT * FROM EmployeeDemographics WHERE LastName Like 'S%'`
#### Wildcards
- `%S%` will give you someone who has an S in their name.
- `S%` will give you someone who has a name beginning with S.
- `%S%o` will give you someone who has and s and ends with an o.
- etc...

### NULL and NOT NULL
- This works with the where statement
- `Select * from EmployeeDemographics where FirstName is Null` OR `Select * from EmployeeDemographics where FirstName is NOT NULL`


### IN, AND, OR
`SELECT * FROM EmployeeDemographics WHERE FirstName = 'Jim' AND FirstName = 'Micheal'...` 
OR we could do this:
`SELECT * FROM EmployeeDemographics WHERE FirstName in ('Jim', 'Micheal')`
We can understand IN as a way of saying equal for multiple things. 

### Group By
`SELECT DISTINCT(Gender) FROM EmployeeDemographics` results in it returning the first distinct Male and Female row. However, if we do `SELECT GENDER FROM EmployeeDemographics GROUP BY Gender`, All of the female attributes get grouped into one and, all of the male attributes get grouped into one. 

`SELECT GENDER, Count(Gender) FROM EmployeeDemographics GROUP BY Gender` will give us the correct count for each respective row. Distince will show us which values are unique by group by allows you to get more details on it.

`SELECT Gender, Age, Count(Gender) From EmployeeDemographics GROUP BY Gender, Age` - will show that there is no person in the database that is the same gender and age. 
> Why do we not include Count(Gender) in the Group By statement as well?

It is a derived value, based off the gender column. Technically it is not a real column in the table but its one we are creating.  

### Order By
- ASC by default 
- Will order by the column given.
- You can also use multiple columns: `SELECT * FROM EmplyeeDemographics ORDER BY Age, Gender.`
- In this situation, it will be ordered by Age first and then by Gender. That means that if you have two employees that are 31, one female and one male, the female one will be listed first. 
- You can also change the order of each one: `SELECT * FROM EmplyeeDemographics ORDER BY Age, Gender DESC.` This will give you the Gender in DESC order - if we use the same example, the male employee will now come first. 
- `SELECT * FROM EmplyeeDemographics ORDER BY Age DESC, Gender DESC.` Now both will be descending
- We also don't have to use column names, you could put numbers instead. 
- `SELECT * FROM EmplyeeDemographics ORDER BY Age DESC, Gender DESC.` = `SELECT * FROM EmplyeeDemographics ORDER BY 4 DESC, 5 DESC.`