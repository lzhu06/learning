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
