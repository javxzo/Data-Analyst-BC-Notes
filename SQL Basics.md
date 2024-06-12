# The Basics - SQL!

## 00:15:08 SQL Basics Tutorial | Installing SQL Server Management Studio and Create Tables
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

### Inserting into table
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

### Select & From Statements

`SELECT * FROM EmployeeSalary` - Gives you all the values in EmployeeSalary
`SELECT FirstName, LastName FROM EmployeeDemographics` - Gives you (ONLY) first and last names from that table. 
`SELECT TOP 5 * from EmployeeDemographics` - Gives you the top 5 rows for all columns.
