# Data-Gathering-Technique-for-Data-Analysis

In data analysis we need to follow 5 steps 
- Asking Question to the stakeholder based on their desire output
- Data Wrangling means `gathering data`,`assessing data` and `cleaning data`
- Exploratory Data Analysis(EDA) like explore and augment the data.
- Drawing Conclusion based on the data
- Make ppt, dashboard,story telling and show it to the stake holder.

Here we will go through the data gathering concept.Sometimes we need to gather data from APIs, web scraping, databases etc. and we may have data in different formats such as CSV, JSON, HTML, and Excel. Here, we will learn how to import and export data in different formats.
### Import Data
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
## TSV(Tab Separated Value)
```python
pd.read_csv('movie_titles_metadata.tsv',sep='\t') 
#if we dont have column and  want to give column name then we can use 
pd.read_csv('movie_titles_metadata.tsv',sep='\t',names=['sno','name','release_year','rating','votes','genres'])

```
I upload a python code to handle CSV data on various scenarios. you can look over this code [here](working-with-csv.ipynb)
## Excel Format
```python
import pandas as pd
pd.read_excel("file_name.xls")
#if we have two sheets and want to access the second sheet then
pd.read_excel("file_name.xls",sheet_name="sheet_name_2")


```
Anyone interested can go through pandas excel [documentation](https://pandas.pydata.org/docs/reference/api/pandas.read_excel.html)
## Text Files(.txt)
 Its look like tsv file so use `read_csv` 
 ```python
pd.read_csv("file_name.txt", sep="\t")
```
## JSON Format
```python
import pandas as pd
df=pd.read_json=("file_name.json")
df.head()

#import json data from url
pd.read_json('https://www.niloy.json')
```
anyone interested can look over the [documentation](https://pandas.pydata.org/docs/reference/api/pandas.read_json.html)

## SQL format
```python
import pandas as pd 
import sqlalchemy
engine = sqlalchemy.create_engine('mysql+pymysql://root:pass@123@localhost:3306/ecommerce')
df = pd.read_sql_table('table_name',engine)
df


#for query we use
query='''

SELECT * from table_name
  
     '''

df = pd.read_sql_query(query,engine)
df
```
### Export the data



