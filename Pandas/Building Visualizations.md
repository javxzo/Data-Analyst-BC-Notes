# Building Visualizations

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
df = pd.read_csv(r'ice cream ratings path')
df.set_index('Date')
```
### Options:
```
df.plot()
```
- bar
- barh (horizontal)
- box (boxplot)
- kde (kernel density estimation plot)
- density (^)
- area (area plot)
- pie
- scatter 
- hexbin
- ...

```
df.plot()
```
Will default to a line plot like so:

![alt text](images\plotimage.png)

```
df.plot(kind = 'line', subplots = True)
```
Will result in:

![alt text](images\plotimage-1.png)

```
df.plot(kind = 'line', title = 'Ice Cream Ratings')
```
Will fix up the title.

```
df.plot(kind = 'line', title = 'Ice Cream Ratings', xlabel = "Daily Ratings", ylabel = "Scores")
```
Will alter the x and y axis titles.

If we do a bar plot:

![alt text](images\plotimage-2.png)

We can also do:

![alt text](images\plotimage-3.png)

with: 
```
df.plot(kind='bar', stacked = True)
```

We can specify which column by adding it at the start:

![alt text](images\plotimage-4.png)

```
df['Flavor Rating'].plot(kind='bar', stacked = True)
```

We can do the same with 'barh'

If we do a scatter plot:
```
df.plot.scatter(x = 'Texture Rating', y = 'Overall Rating', s = 100)
```
Where s is size...

![alt text](images\plotimage-5.png)

c = 'Yellow' will make it yellow :D.

If we do a histogram:
```
df.plot.hist()
```
By default (with 10 columns):

![alt text](images\plotimage-6.png)

We can alter it by doing df.plot.hist(20)

If we use a box plot:

df.boxplot()

![alt text](images\plotimage-7.png)

I do not like these. Shows minimum and maximum as well as the 25%, 50% and 75%.

-_-

If we do area plots:

![alt text](images\plotimage-8.png)

FIG SIZE MAKE IMG BIGGER.

pie chart:

```
df.plot.pie(y='Flavor rating')
```

Customizable with colors and size.

This video won't end.

You can change what visual a graph is. 
```
print(plt.style.available)
```
Shows us all the different types of styling:
```
plt.style.use('insert style name here')
```
