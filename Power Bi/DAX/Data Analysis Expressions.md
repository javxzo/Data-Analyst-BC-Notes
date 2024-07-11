### DAX
- starting by loading up the dataset
- we are going to go to our fields, right click a table name and click new measure.
- ![alt text](images\image.png)
- We open up a bar - similar to the top on on excel with "Measure =", we can change measure to be whatever we want the name to be. 
  - Count of Sales = COUNT('Apocolypse Sales'[Order ID])
- We can click enter, click on the box next to it to take a look at it. 
- ![alt text](images\image-1.png)
- We can see how many people are buying the products. We want to see who's buying. 
- We add customer and move it on top of sales in columns. 
- ![alt text](images\image-2.png)

### Highest Selling Product
- We select produce name from under Apoc. Store.
- We create a new measure underneath Apoc. **Sales** as Sum Of Products Sold = Sum('Apocolypse Sales'[Units Sold])
- ![alt text](images\image-3.png)

### Aggregator/Iterator Functions
- If you add x to some of the aggregate functions, it will turn them into an iterator function.
- SUMX, AVERAGEX...
- We start by creating a new measure under Apoc. Store. 
- Profit = (Sum('Apocolypse Store'[Price]) - SUM('Apocolypse Store'[Production Cost])) * SUM('Apocolypse Sales'[Units Sold])
- ![alt text](images\image-4.png)
- Now, lets look at the difference bewteen SUM and SUMX
- ![alt text](images\image-5.png)
- When we create a new column for this table and add a profit column, we see that it results in the same value everytime.
- What we want it to do is see the price for item sold and calculate that to give us the profit for each row. 
- What we need to do is use SUMX. 
- ![alt text](images\image-6.png)
- Note: we removed the other "SUM" in the equation.

### Date Functions
![alt text](images\image-7.png)
- We can create a new column and use different functions to give us more information about the date.
- In this case, we are looking at WEEKDAY. The option after for "1,2,3" will tell u about the different options.
  - Ex. Monday = 1, Sunday = 7 etc.
- Tells us which day of the week we are seeing more purchases on.
![alt text](images\image-8.png)
- We can create a graph and see trends in the data (especially with bigger sets of data)

### IF statements
- Works the same as excel - can refer to that note. 
