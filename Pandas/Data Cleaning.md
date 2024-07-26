## Data Cleaning

Using Customer Call List. Need to clean it up so it's easier to utilize. Want to remove useless columns. 

At a brief overview:
- Phone number needs to be standardized
- Address needs to be standardized
- Paying Customer needs to be standardized.
- Not Useful Column can be removed
- Do Not Contact, needs to be standardized AND we should get rid of the ones that say Yes. 

1. Remove duplicates
```
df = df.drop.duplicates()
```
- Row 19 and 20 were the exact same, row 20 is removed

2. Remove unecessary columns
- We want to take out Not_Useful_Column
```
df = df.drop(columns = 'Not_Useful_Column')
or 
df.drop(columns = 'Not_Useful_Column', in place = True)
```

3. Last Name correction
- We have null values, random characters, etc.
- We want to specifically do it to the last name column.
```
df['Last_Name'].str.strip()
```
By default, it won't remove any of the characters that we want it to - only spaces. We need to specify the characters that we want to remove.
```
**df['Last Name']** = df['Last_Name'].str.lstrip("...")
```
Note that it **must** be **df['Last Name'] =** because if we only did df =, we would make the df equal to the column.
If there was a value in the middle, it wouldn't work. We could use replace instead.
```
**df['Last Name']** = df['Last_Name'].str.strip(["123./])
```
All of the characters can be removed with the above statement. The first instinct was to put them all in a list but all the values become NaN due to REGEX functionality. We need to put it all in one string. 

4. Phone Number
We want all of them to follow the xxx-xxx-xxxx format. We need to start by getting rid of all the non numeric values. 
```df['Phone_Number'] = df['Phone_Number'].str.replace('[^a-zA-Z0-9]', '')```
What the carrot (^) is doing is saying that we are going to return anything except a-z or A-z or 0-9. 
- The only remaining letters are all Na and NaN - we will turn this to null later
- Now the goal is to format this.
```
df['Phone_Number'].apply(lambda x: x[0:3] + '-' + x[3:5] + '-' + x[6:10])
```
This pulls an error because we are treating the value as a string when there are values (in the data) that are floats. So to fix this, we need to change the entire column to be strings. 
```
df['Phone_Number'] = df['Phone_Number'].apply(lambda x: str(x))
```
All of our values become strings
Now we can try running this again: 
```
df['Phone_Number'] = df['Phone_Number'].apply(lambda x: x[0:3] + '-' + x[3:5] + '-' + x[6:10])
```
And it will work!
```
df["Phone Number"].str.replace('nan--', '')
df["Phone Number"].str.replace('Na--', '')
```
This one is used to clean out the remaining nan and Na values.

5. Address
- Our 'boss' says to split it up into three different columns to make it easier. 
- Note: the data is split by commas
```
df[['Street_Address', 'States', 'Zip_Code']] = df['Address'].str.split(",", 2, expand = True)
```
We are now creating three columns for street address, states and zip code. The OG Address is untouched. The split parameters go by (character using to split, how many times, extra params).

6. Yes and No and Y and N and ... (in Paying Customer and DNC)
```
# df["Paying Customer"].str.replace('Y', "Yes") # this wont work because the Yes will become YeYes.

df["Paying Customer"] = df["Paying Customer"].str.replace('Yes', "Y")
df["Paying Customer"] = df["Paying Customer"].str.replace('No', "N")
```
Same for DNC.

7. Getting rid of NaN/Null/N/a
```
df = df.replace('N/a', '')
```
NaN is not a number - can't use df = df.replace('NaN', '')
We can solve this by doing...
```
df.fillna('')
```

8. Do not Contact/Phone Removal
We don't want to provide the numbers that have Y for Do_Not_Contact.
```
for x in df.index:
    if df.loc[x, 'Do_Not_Contact'] == 'Y':
        df.drop[x, inplace = True]
```
We want to the same for the phone numbers that are empty. 
```
for x in df.index:
    if df.loc[x, 'Phone_Number'] == '':
        df.drop[x, inplace = True]
```
OR
```
df.dropna(subset='Phone_Number', inplace = True)

9. Reset the index
```
df.reset_index(drop=True)
```
yahoo.

10. All done!