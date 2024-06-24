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

### XLOOKUP
- Searches a range or an array for a match and returns the corresponding item from a second range or array
- XLOOKUP(box you are looking for, column looking through, column that it will return in the case it is found)
  - Example: =XLOOKUP(A4, H2:H10 (Name Column), O2:O10 (Email Column))
    - This will look through the name column, if there is a match then it will return the email of that person. 

### XLOOKUP Multiple Rows
- Same idea but you can return multiple rows - like adding the end date. 
- Example: =XLOOKUP(A4, H2:H10 (Name Column), O2:P10 (Email and EndDate Column))
  - This will look through the name column, if there is a match then it will return the email and end date of that person. 
- Will return both
- You can only do this if they are both right next to each other.

### XLOOKUP Exact Match
- Same formula:
- Example: =XLOOKUP(A4, H2:H10 (Name Column), O2:O10 (Email Column), "Not Found")
- This will look through the name column, if there is a match then it will return the email of that person.
- In this case, it would return not found. 

- XLOOKUP("*"&A4, H2:H10, O2:O10, "Not Found", 2)
- Anything that comes before A4 is okay

### XLOOKUP Search Order
- Will give you options for exact match, next largest or next smallest. 
- Done by adding commas to the end (with a number value)
- XLOOKUP(A4, H2:H10, O2:O10, "Not Found",,) - exact, next smallest/largest, wildcard
- XLOOKUP(A4, H2:H10, O2:O10, "Not Found",,,) - search first to last, last to first, binary search (sorted ascending order), binary search (sorted descending order)

### XLOOKUP Horizontal
- same idea as vertical - need to be cautious in selecting columns

### XLOOKUP with SUM
- =SUM(XLOOKUP(I1, H1:S1, H2:S2):XLOOKUP(J1, H1:S1, H2:S2))

### VLOOKUP
- VLOOKUP(lookup value, table array, column number of the value you want returned, what kind of match do you want)
  - table array is a area you are searching through (not column)
- messy with adding columns - need to adjust formula. Doesn't need to be done with XLOOKUP

