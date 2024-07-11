### Opening up new data
- Using pivot tables and purchase overview instead -> transform data
![alt text](Images\image.png)

### Starting With Data Cleaning
- Want to start by getting rid of those top two rows.
- ![alt text](Images\image-1.png)
- Note that the first column now has the header titles that we actually wanted - Location, Products, Date...
- ![alt text](Images\image-2.png)
- This can be done by using the "Use First Row as Headers"
- When we did this, we will also notice under applied steps that we changed type. Originally, the date column had a datatype of alphanumerical, but now its switched to double(decimal) as all the values are a consistent type.
- We are going to change it so that its fixed decimal type as we are working with money. 
- ![alt text](Images\image-3.png)
- Next, we notice the subtotals (as well as the grand total) within the actual data:
- ![alt text](Images\image-4.png)
- We try to do this with filtering! We can do this by removing emptys.
- ![alt text](Images\image-5.png)
- We are going to do is remove the grand total column by going into home, remove columns (after selecting which one)
- At the moment, our column names are dates. While this looks fine visually, it'll be difficult when visualizing the data. We want to transpose this or pivot this so that these dates are actually rows. 
- We click on the first date through the last date (shift), head to the transform tab, and click unpivot columns. 
- ![alt text](Images\image-6.png)
- Finalizing it by changing datatypes and column names. 

### Working on the Pivot Table
- starting with our pivot table, we are going to transform the first row as our column titles. 
- If we were to unpivot the following columns and turn the data type to date, it wouldn't work. It becomes unusable - need to watch out for.
- ![alt text](Images\image-7.png) 

### Close and apply...

