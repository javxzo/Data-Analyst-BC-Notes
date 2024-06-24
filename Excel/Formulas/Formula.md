# Basic Formulas in Excel

### Max-Min
- Starting off in a cell with "=" incidicates to Excel you are going to be using a formula
- The MAX(...) will give the mav value, the lastest date, the oldest age etc.
- The MIN works in the same way of the opposite manner. 

### If and Ifs
- If this, then that
- if this, if this, if this...

### Len
- works as expected, gives the length of whatever value inputted

### Left and Right
- similar to substrings
- left(column, number of values you want to keep)
  - left(firstName, 3) turns dwight into dwi
- right works to the same extent
- Right(date, 4) will give us the year

### Date To Text
- =TEXT(H2, "dd/mm/yyyy") will give us the text version of the date so that we can perform other string functions on it.

### Trim
- extra spaces, raw data, dirty data
- =Trim(Range) = cleaned up data

### Concatenate
- add two strings together, joined together
- = concatenate (B2, " ", C2) -> generating emails, full names...

### Substitute
- Useful for different formats of the same thing like dates
- 10-03-2000 versus 10/03/2000
- =Substitute(range, "-", "/")
- =Substitute(range, "-", "/", 1) -> instance num will tell you which instance to change.

### Sum
- Adds all values 

### SUMIF
- =SUMIF(range(salary), ">50000")
  - Will only add if the salary is greater than value

### SUMIFS 
- same idea
- SUMIF(salary, gender, "Female", Age, ">30")
  - will add if the person is female and over the age of 30.

### Count
- How many cells are there
- COUNTIF and COUNTIFS works the same way

### Days-NetworkDays
- Days will give you number of days from start date to end date.
- Days(end date, start date)
- NetworkDays takes out weekends and holidays.