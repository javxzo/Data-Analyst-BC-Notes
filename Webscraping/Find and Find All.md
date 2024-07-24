# Find and Find_All

Let's start with what we already know so far:

```
from bs4 import BeautifulSoup
import requests
url = 'https://www.scrapethissite.come/pages/forms'
page = requests.get(url)
soup = BeautifulSoup(page.text, 'html')
print(soup)
```

If we try doing:
```
soup.find('div')
```
We end up with the very first div tag in our HTML.

If we try doing:
```
soup.find_all('div')
```
We end up with all the div tags in our HTML.

We can take note of the different classes in each of our div tags. As well as the different a tags. We can filter down off of these.

```
soup_find.all('div', class_='col-md-12')
```
This can find all the div's where class is equal to 'col-md-12'

```
soup_find.all('p', class_='lead').text
```
Results in a common error because 'find_all' does not have a text attribute. We need to use find. 

```
soup_find('p', class_='lead').text.strip()
```
Will result in what we want! 

