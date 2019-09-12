#### Importing data in python
* Reading a text file
  ```python
  filename = 'sample_file.txt'
  file = open (filename, mode = 'r') # 'r' is to read
  text = file.read()
  file.close()
  print(text)
  ```
* Writing to a file
  ```python
  filename = 'sample_file.txt'
  file = open (filename, mode = 'w') # 'w' is to write
  text = file.read()
  file.close()
  print(text)
  ```
> Example:
```python
# Open a file: file
file = open('moby_dick.txt', mode='r')

# Print it
print(file.read())

# Check whether file is closed
print(file.closed)

# Close file
file.close()

# Check whether file is closed
print(file.closed)

```
```python
# Read & print the first 3 lines
with open('moby_dick.txt') as file:
    print(file.readline())
    print(file.readline())
    print(file.readline())
```
* Flat files: Header
* Two main packages: NumPy and pandas

##### Importing flat files using NumPy
NumPy arrays: standard for storing numerical data; Essential for other packages:e.g. scikit-learn；
> Syntax: 
  ```python
  import numpy as np
  filename = ‘MNIST.txt'
  data = np.loadtxt(filename, delimiter=',' skiprow='1', usecols=[x:x], dtype=str)
  ```
##### Importing using pandas
>Example
  ```python
  # Assign the filename: file
file = 'digits.csv'

# Read the first 5 rows of the file into a DataFrame: data
data = pd.read_csv(file, nrows=5, header=None)

# Build a numpy array from the DataFrame: data_array
data_array = data.values

# Print the datatype of data_array to the shell
print(type(data_array))
  ```
>Example
```python
# Import matplotlib.pyplot as plt
import matplotlib.pyplot as plt

# Assign filename: file
file = 'titanic_corrupt.txt'

# Import file: data
data = pd.read_csv(file, sep='\t', comment= '#', na_values='Nothing')

# Print the head of the DataFrame
print(data.head())

# Plot 'Age' variable in a histogram
pd.DataFrame.hist(data[['Age']])
plt.xlabel('Age (years)')
plt.ylabel('count')
plt.show()
```
#### Importing other file types
* Pickled files
```python
import pickle
with open ('','rb') as file:
    data = pickle.load(file)
print(data)
```
* importing Excel Spreadshetts
```python
import pandas as pd
file = 'file.xlsx'
data = pd.ExcelFile(file)
print(data.sheet_names)
df1 = data.parse('1960-1966')
df2 = data.parse(0)
```
>Example:
```python
# Import pandas
import pandas as pd

# Assign spreadsheet filename: file
file = 'battledeath.xlsx'

# Load spreadsheet: xl
xls = pd.ExcelFile(file)

# Print sheet names
print(xls.sheet_names)
```
#### Importing SAS/Stata files
> SAS files: 
  ```python
  import pandas as pd
  from sas7bdat import SAS7BDAT
  with SAS7BDAT('file_name.sas7bdat') as file:
        df_sas = file.to_data_frame()
  ```
> Stata files:
  ```python
  import pandas as pd
  data = pd.read_stata('file_name.dta')
  ```
> HDF5 files: large quantities of numerical data - 100 gb or larter
  ```python
  import h5py
  filename = 'file_name.hdf5'
  data = h5py.File(filename, 'r') # 'r' is to read
  print(type(data))
  
  for key in data.keys():
     print(key)
  #Example
  for key in data['meta'].keys():
      print(key)
  ```
  * Example:
  ```python
  # Import packages
import numpy as np
import h5py

# Assign filename: file
file = 'LIGO_data.hdf5'

# Load file: data
data = h5py.File(file, 'r')

# Print the datatype of the loaded file
print(type(data))

# Print the keys of the file
for key in data.keys():
    print(key)
  ```
#### Importing MATLAB
```python
scipy.io.loadmat() - read .mat files
scipy.io.savemat() - write .mat files

import scipy.io
filename = 'file.mat'
mat = scipy.io.loadmat(filename)
print(type(mat))
```
#### Creating a database engine 
* SQLAlchemy
```python
from sqlalchemy import create_engine
engine = create_engine('sqlite://northwind.sqlite')

table_names = engine.table_names() #Including all table names
```
>Example:
```python
# Import necessary module
from sqlalchemy import create_engine

# Create engine: engine
engine = create_engine('sqlite:///Chinook.sqlite')

# Save the table names to a list: table_names
table_names = engine.table_names()

# Print the table names to the shell
print(table_names)
```
* Querying relational database in python
```python
#your first sql query

from sqlalchemy import create_engine
import pandas as pd
engine = create_engine('sqlite:///northwind.sqlite')
con = engine.connect()
rs = con.execute("SELECT * FROM Orders")
df = pd.DataFrame(rs.fetchall())
df.columns = rs.keys()
con.close()
print(head())
```
>Example_1
```python
# Import packages
from sqlalchemy import create_engine
import pandas as pd

# Create engine: engine
engine = create_engine('sqlite:///Chinook.sqlite')

# Open engine connection: con
con = engine.connect()

# Perform query: rs
rs = con.execute("select * from Album")

# Save results of the query to DataFrame: df
df = pd.DataFrame(rs.fetchall())

# Close connection
con.close()
```
>Exampe_2
```python
# Open engine in context manager
# Perform query and save results to DataFrame: df
with engine.connect() as con:
    rs = con.execute("SELECT LastName, Title from Employee")
    df = pd.DataFrame(rs.fetchmany(3))
    df.columns = rs.keys()

# Print the length of the DataFrame df
print(len(df))

# Print the head of the DataFrame df
print(df.head())

df = pd.read_sql_query("SELECT * FROM Orders", engine)
```
##### Import data from Web
* urllib: urlopen() - accept url instead of files
  ```python
  from urllib.request import urlretrieve
  url = 'http://link.csv'
  urlretrieve(url, 'filename.csv')
  ```
 
 #### Retriving data from open database (API & JSON)
 ```python
#Retriving data from web portal 
import requests
 url = 'open_source_url'
 r = requests.get(url)
 json_data = r.json()
 for key, value in json_data.items():
      print(key + ':', value)
 #Example of URL
 #'http://www.omdbapi.com/?t=hackers' Retrun data for a movie with title(t) 'Hackers'
 #following is the example
 # Import requests package
import requests

# Assign URL to variable: url
url = 'http://www.omdbapi.com/?apikey=72bc447a&t=the+social+network'

# Package the request, send the request and catch the response: r
r = requests.get(url)

# Print the text of the response
print(r.text)
 ```


