## Filtering and Ordering

```
import pandas as pd
df = pd.read_csv(r'path\to\world_population.csv')

df[df['Rank'] ,= 10] # Will return all the countries that have a rank less than 10
```
specific_countries = ["Bangladesh", "Brazil"]
df[df['Country'].isin(specific_countries)]
```

### More functions
```
df[df['Country'].str.contains('United')]

df2 = df.set_index('Country')
df2.filter(items = ['Continent', 'CCA3']) #items will show you the columns you want
df2.filter(items = ['Continent', 'CCA3'], axis = 0) 

df2.filter(like = 'United', axis = 0) 
df2.loc['United States'] will return all the values for the United States.
```

### Order by
```
df[df['Rank']<10].sort_values(by='Rank', ascending = False)
```
or 
```
df[df['Rank']<10].sort_values(by=['Rank', 'Country'], ascending = False)
```
Will order by Rank first and then, Country. 
```
df[df['Rank']<10].sort_values(by=['Rank', 'Country'], ascending = [False, True])
```
