# Starting Pandas
### .csv files
```
import pandas as pd 
df = pd.read_csv(r'path_of_csv.csv')
```
When using pandas, it calls in the data as a dataframe. 
We need to assign this to a variable.

### .txt files
If we are to import a .txt, we would need a seperator. 
```
df = pd.read_csv(r'path_of_txt.txt', sep = '\t')
```
This is one way to do it but the correct way to do it is like this:
```
df = pd.read_table(r'path_of_txt.txt')
```

### JSON files
```
df = pd.read_JSON(r'path_of_JSON.JSON')
```

### Excel Files
```
df = pd.read_excel(r'path_to_sheet.xlxs')
```
If you have multiple sheets, you can specify by saying:
```
df = pd.read_excel(r'path_to_sheet.xlxs', sheet_name = "sheet 2")
```

### Options, info:
You can also adjust other options for your data. An example:
```
pd.set_option('display.max.rows', 235)
pd.set_option('display.max.columns', 40)
```
See more information about your data:
```
df.info()
df.shape() # shows columns and rows
df.head()
df.head(10)
df.tail()
df['col name']
df.loc[224] # like the column name
df.iloc[225] # integer location even if the first column changes
```

