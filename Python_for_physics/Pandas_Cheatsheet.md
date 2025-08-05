# Pandas Cheatsheet

## What is a DataFrame?
A **DataFrame** is a two-dimensional, tabular data structure in Pandas. It is similar to an Excel spreadsheet or an SQL table, consisting of rows and columns. Each column in a DataFrame is a **Series**, and it can hold different data types (e.g., integers, floats, strings).

### Anatomy of a DataFrame
A Pandas DataFrame consists of three main components:

1. **Index** – The labels for each row (default is integer-based).
2. **Columns** – The names of the data fields (headers).
3. **Values** – The actual data stored in the DataFrame.

#### Example DataFrame:
```python
import pandas as pd

data = {'Name': ['Alice', 'Bob', 'Charlie'], 'Age': [25, 30, 35], 'City': ['NY', 'LA', 'Chicago']}
df = pd.DataFrame(data)
print(df)
```

**This results in:**
```
     Name  Age     City
0   Alice   25       NY
1     Bob   30       LA
2  Charlie   35  Chicago
```

### Breakdown:
```
Index   Name     Age   City
---------------------------
0       Alice    25    NY
1       Bob      30    LA
2       Charlie  35    Chicago
```

- **Index (leftmost column)**: Identifies each row (0, 1, 2 by default).
- **Columns (header row)**: Name, Age, City.
- **Values (data cells)**: The actual data under each column.

---

## What is a Series?
A **Series** is a one-dimensional array in Pandas that can hold any data type. It is similar to a single column in a DataFrame.

### Anatomy of a Series
A Pandas Series consists of two main components:

1. **Index** – Labels for each row (default is integer-based).
2. **Values** – The actual data stored in the Series.

#### Example Series:
```python
import pandas as pd

data = ['Alice', 'Bob', 'Charlie']
series = pd.Series(data)
print(series)
```

**This results in:**
```
0     Alice
1       Bob
2  Charlie
dtype: object
```

### Breakdown:
```
Index   Value
----------------
0       Alice
1       Bob
2       Charlie
```

A Series can also have custom index labels:
```python
series = pd.Series(data, index=['a', 'b', 'c'])
print(series)
```
**This results in:**
```
a     Alice
b       Bob
c  Charlie
dtype: object
```

---

## Inspecting Data
```python
df.head()  # First 5 rows
df.tail()  # Last 5 rows
df.info()  # Summary of the DataFrame
df.describe()  # Statistics for numerical columns
df.shape  # (rows, columns)
df.columns  # List of column names
df.dtypes  # Data types of each column
```

---

## Selecting Data
**Selecting columns:**
```python
df['Name']  # Returns a Series
df[['Name', 'Age']]  # Returns a DataFrame
```

**Selecting rows by index:**
```python
df.iloc[0]  # First row
df.loc[0]  # First row (explicit index)
df.iloc[0:2]  # First two rows
df.loc[df['Age'] > 25]  # Rows where Age > 25
```

---

## Combining DataFrames (Merging and Concatenation)
Merging and concatenation allow you to combine DataFrames based on different criteria.

### Merging DataFrames
```python
df1 = pd.DataFrame({'ID': [1, 2], 'Name': ['Alice', 'Bob']})
df2 = pd.DataFrame({'ID': [1, 2], 'Salary': [50000, 60000]})
df_merged = pd.merge(df1, df2, on='ID')
```

**This results in:**
```
   ID   Name  Salary
0   1  Alice   50000
1   2    Bob   60000
```

### Diagram:
```
df1:
ID   Name
------------
1    Alice
2    Bob

df2:
ID   Salary
------------
1    50000
2    60000

Merged DataFrame:
ID   Name   Salary
--------------------
1    Alice   50000
2    Bob     60000
```

### Concatenating DataFrames
Concatenation stacks DataFrames either **vertically** (by rows) or **horizontally** (by columns).

#### Example: Concatenating by Rows (Adding More Data)
```python
df1 = pd.DataFrame({'A': [1, 2], 'B': [3, 4]})
df2 = pd.DataFrame({'A': [5, 6], 'B': [7, 8]})
df_concat = pd.concat([df1, df2], ignore_index=True)
```

**This results in:**
```
   A  B
0  1  3
1  2  4
2  5  7
3  6  8
```

#### Example: Concatenating by Columns (Adding More Features)
```python
df3 = pd.DataFrame({'C': [9, 10]})
df_concat_col = pd.concat([df1, df3], axis=1)
```

**This results in:**
```
   A  B   C
0  1  3   9
1  2  4  10
```

---

## Splicing DataFrames
Splicing allows you to extract subsets of rows and columns from a DataFrame.

### Selecting Specific Rows and Columns
```python
df.iloc[0:2, 0:2]  # Select first 2 rows and first 2 columns
df.loc[0:1, ['Name', 'Age']]  # Select first two rows by index and specific columns
```

### Diagram:
```
Original DataFrame:

Index   Name     Age   City
---------------------------
0       Alice    25    NY
1       Bob      30    LA
2       Charlie  35    Chicago

Splicing:
Selecting first two rows and two columns ->

Index   Name     Age
--------------------
0       Alice    25
1       Bob      30
```

---

## Exporting and Importing Data
**Reading CSV:**
```python
df = pd.read_csv('data.csv')
```

**Writing to CSV:**
```python
df.to_csv('output.csv', index=False)
```

---

This cheatsheet provides a quick reference for using Pandas in Python for data manipulation and analysis.
