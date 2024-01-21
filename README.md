# Data-Gathering-Technique-for-Data-Analysis

In data analysis we need to follow 5 steps 
- Asking Question to the stakeholder based on their desire output
- Data Wrangling means `gathering data`,`assessing data` and `cleaning data`
- Exploratory Data Analysis(EDA) like explore and augment the data.
- Drawing Conclusion based on the data
- Make ppt, dashboard,story telling and show it to the stake holder.

Here we will go through the data gathering concept.Sometimes we need to gather data from APIs, web scraping, databases etc. and we may have data in different formats such as CSV, JSON, HTML, Excel. Here, we will learn how to import and export data in different formats.
## CSV(Comma Separated Value) 
Anyone interested can look over this pandas read_csv [documentation](https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html)
```python
import pandas as pd
# import local csv file
df=pd.read_csv("file_name.csv")
#import csv file from an URL
import requests
from io import StringIO

url = "https://file_name.csv"
headers = {"User-Agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.14; rv:66.0) Gecko/20100101 Firefox/66.0"}
req = requests.get(url, headers=headers)
data = StringIO(req.text)

pd.read_csv(data)


```
