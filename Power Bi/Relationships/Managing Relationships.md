### Working with the Model Tab
![alt text](images\image.png)
- There are already relationships that Powerbi has automatically detected and created. 
-  Double clicking the line on the relationships between two tables will result in this tab here:
![alt text](images\image-1.png)
- We have a one to many relationship. There's only one or a single crossfilter direction. 
- When we open apocolypse sales and customer information, both the tables are set on customers instead of customer id - change that.

### Cardinality
![alt text](images\image-2.png)
In this case, the Customer ID table is much smaller and only has one row per customer. The Sales table is much larger and can have multiple sales per customer. Thus explaining why the cardinality is M:1.

### Cross Filter Direction
- There are only two options there - single or both. When we keep it at a single direction, we won't be able to access the other table(s). 
- Changing both of the options to "both", we can now access all the data amongst the three tables in relation to each other.

### Active Relationships
- Selecting this option means that this is going to be the default relationship between these tables. 
- It means that Power Bi will use this relationship by default in calculations and visualizations involving the related tables. 
- Only one active relationship between any two tables (on Power Bi).
- Allows for more accurate filtering and cross-filtering. 

### Building Relationships from Scratch
- if we go ahead and delete the relationships between the three tables, we can start reconnecting them by dragging customer information's customer id box to the apocalypse sales' cust id. 
- We can do the same to product id in store and sales.
- Change both the cross filters to both.