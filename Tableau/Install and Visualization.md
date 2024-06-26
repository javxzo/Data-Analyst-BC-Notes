# Starting with Tableau!

- Using Tableau public! (https://public.tableau.com/app/discover)
- Using the following dataset! (https://www.kaggle.com/datasets/gregorut/videogamesales - also added to folder)

Note that it is a CSV, so we will be uploading it onto tableau as a textfile and not as an excel sheet. 

![alt text](images\image.png)

This is our landing page. If you add more files, you can frag them to that center area and connect them. Sheet1 (at the bottom left) has everything we are starting with. 

![alt text](images\image-1.png)

The graphs on the right will start to become more visible as we add data onto our sheet. 

Dimensions - before the line on the left column. (Typically strings)
Measures - below the line on the left column.  (Typically numerical)

You can drag and drop your dimensions/measures into your row and columns sections or straight in the middle - tableau will try it's best to define it itself.

### Marks
- Contains color, size, text, detail, toolkit. 
  ![alt text](images\image33.png)
- If we add `Genre` into rows or columms, the graph splits up into many sections. If we add it to `Marks`, it all layers. 
- This is where the attributes become super helpful. We can split it up into different colors. 
- Select on the lil three dots next to Genre > choose color. 
![alt text](images\image-4.png)
- Note that label can be edited in multiple ways - min-max, scope...

### Filters
![alt text](images\image-5.png)
- We've selected to filter out by platform. Similar to the pivot table functions on Excel, we can choose what information we want to include or that we don't want to include. 

### Making a dashboard
- Now we take a look at combining the previous one with this one:
  ![alt text](images\image-6.png)
- New Dashboard is an option available at the bottom. 
- Change size to automatic
- 