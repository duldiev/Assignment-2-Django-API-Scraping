# Assignment-2-Django-API-Scraping
## Installation

First, set up your project with django by creating app and templates.

If you have pip on your system, you can simply install **selenium**, **BeautidulSoup 4**, using these following:
```
pip install -U selenium
```
```
pip install bs4
```

It also requires [geckodriver](https://github.com/mozilla/geckodriver/releases)

To get the data from https://etherscan.io/accounts, we need to register and create new API Key to fully access to API.

Charts are created by Chart.js library.

We also need to use webdriver package to page 100 accounts visible and scrape them.

## Usage
* Import those libraries
* Open a new Firefox browser
* Load the page at the given URL
### Example 1
```
from bs4 import BeautifulSoup
from selenium import webdriver

url = 'https://etherscan.io/accounts'
driver = webdriver.Firefox()
driver.get(url)
```
* Parse the web page using BeautifulSoup as soup
* Toke the news articles using findAll() method
* Print them out taking only text that is inside tags
### Example 2
BeautifulSoup is used to scrape lines that placed in 'a' tag.
```
page = driver.page_source

soup = BeautifulSoup(page, 'html.parser')

attrs = soup.find_all('a')
```

### Example 3
All the addresses and balances a stored in sqlite3 that is integrated with Django project. You can also manage the data and add new data by accessing the admin page.

Because the balance number is too long, there is an algorithm that divides huge number by small integer. The balance that we get from API is returned in wei, but we can convert it to ether as shown in the example. 
```
ether = longDivision(longDivision(longDivision(address['balance'], 1000000), 1000000), 1000000)
a = Address(account=address['account'], balance=ether)
a.save()
```
