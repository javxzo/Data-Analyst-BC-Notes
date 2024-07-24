# Beautiful Soup + Requests

```
from bs4 import BeautifulSoup
import requests
```

Specify where we are taking the html from:

```
url = 'https://www.scrapethissite.com/pages/forms/'
page = requests.get(url)
```
We got a response of 200 - good!
204 - no content, 400 - bad request, 404 - server cant be found.

Now, we need to focus on what specifically we want from the page:

Page is what sends the request and then the .text is what's retrieving the actual raw HTML that we're going to be using.
The second parameter in the following chooses how you want the information to be parsed. 
```
soup = BeautifulSoup(page.text, 'html')
```
Make soup equal to that information right there.

If we are to print the soup, we can see all the information thats available in the html.

We can also do:
print(soup.prettify()) -> will make it easier to look at (adds a hierarchy)


