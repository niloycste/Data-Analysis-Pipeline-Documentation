# Data-Pipeline-Technique-for-Data-Analysis

# Data Gathering Technique
In data analysis we need to follow 5 steps 
- Asking Question to the stakeholder based on their desire output
- Data Wrangling means `gathering data`,`assessing data` and `cleaning data`
- Exploratory Data Analysis(EDA) like explore and augment the data.
- Drawing Conclusion based on the data
- Make ppt, dashboard,story telling and show it to the stake holder.

Here we will go through the data gathering concept.Sometimes we need to gather data from APIs, web scraping, databases etc. and we may have data in different formats such as CSV, JSON, HTML, and Excel. Here, we will learn how to import and export different formats data.
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
### Export/save the data
**CSV**
```python
df.to_csv("new_file.csv",index=False)
```
**Excel**
```python
df.to_excel("new_file.xlsx")
#if we have multiple sheet then we use `ExcelWriter`
  with pd.ExcelWriter('output.xlsx') as writer:  
     temp_df.to_excel(writer, sheet_name='Sheet_name_1')
     temp_df2.to_excel(writer, sheet_name='Sheet_name_2')
```

**HTML**
```python
df.to_html("file_name.html")
```
**Json**
```python
df.to_json("file_name.json")
```
**SQL**
```python
df.to_sql("file_name",con=engine,if_exists='append')
```

## Working with API
Working with APIs (Application Programming Interfaces) involves making requests to web servers to retrieve or send data. Python provides the requests library, which is commonly used for interacting with APIs.
```python
import pandas as pd
import requests
response = requests.get('https://api.themoviedb.org/3/movie/top_rated?api_key=8265bd1679663a7ea12ac168da84d2e8&language=en-US&page=1') # get api url

temp_df = pd.DataFrame(response.json()['results'])[['id','title','overview','release_date','popularity','vote_average','vote_count']]
pd.DataFrame(response.json()['results'])

# to extract specific information from api
df=pd.DataFrame() #Empty dataframe
for i in range(1,429):
    response = requests.get('https://api.themoviedb.org/3/movie/top_rated?api_key=8265bd1679663a7ea12ac168da84d2e8&language=en-US&page={}'.format(i))
    temp_df = pd.DataFrame(response.json()['results'])[['id','title','overview','release_date','popularity','vote_average','vote_count']]
    df = df.append(temp_df,ignore_index=True)

#save the data into csv
df.to_csv('movies.csv')


```
## Working With Scrapping
web scraping typically involves extracting information from websites.If the company doesn't provide us with API, we will use web scrapping. Python offers several libraries that are commonly used for web scraping, such as BeautifulSoup,selenium for parsing HTML, and requests for making HTTP requests. Anyone interested to see the scraping using selenium can see this [code](Firefox-Scraper.py) 

# Data Assessing & Cleaning
In this step, the data is to be understood more deeply. Before implementing methods to clean it, you will need to have a better idea of what the data is about.<br/>
There are 2 kinds of unclean data.

**Dirty Data:** 
Dirty data, also known as low quality data. Low quality data has content issues.<br/>
- Duplicated data
- Missing Data
- Corrupt Data
- Inaccurate Data

**Messy Data:**
Messy data, also known as untidy data. Untidy data has structural issues.Tidy data has the following properties:<br/>
- Each variable forms a column
- Each observation forms a row
- Each observational unit forms a table

To get more details go through this [python notebook](data_assessing_and_cleaning.ipynb)








