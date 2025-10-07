# Pandas
 Pandas
# 🧠 What is Pandas?

Pandas is a Python library used for data analysis and manipulation.
It allows you to:

Handle tabular data (like Excel or CSV files)

Perform data cleaning, filtering, sorting, and aggregation

Analyze large datasets easily


It’s built on top of NumPy and integrates well with Matplotlib, Scikit-learn, etc.

To start using pandas:

```bash
import pandas as pd

```


---

# 📘 Main Data Structures

## 1. Series – One-dimensional labeled array

### Example:

``` bash
import pandas as pd

# Creating a Series
s = pd.Series([10, 20, 30, 40, 50], index=['a', 'b', 'c', 'd', 'e'])
print(s)
```

### Output:

``` bash
a    10
b    20
c    30
d    40
e    50
dtype: int64
```

---

## 2. DataFrame – Two-dimensional table (rows + columns)

### Example:

```bash
data = {
    'Name': ['Ujjawal', 'Rohan', 'Priya'],
    'Age': [20, 22, 19],
    'Marks': [85, 90, 95]
}

df = pd.DataFrame(data)
print(df)
```

### Output:

```bash
Name  Age  Marks
0  Ujjawal   20     85
1    Rohan   22     90
2    Priya   19     95
```

👉 A DataFrame is like an Excel sheet or SQL table.


---

# 📂 Reading and Writing Data

## Read data:

```bash
# Read from CSV file
df = pd.read_csv("data.csv")
```

## Write data:

```bash
# Save DataFrame to CSV file
df.to_csv("output.csv", index=False)
```


---

# 🔍 DataFrame Basic Operations

## 1. View top and bottom rows

```bash
print(df.head())   # First 5 rows
print(df.tail())   # Last 5 rows
```


---

## 2. Get info about data

```bash
print(df.info())
print(df.describe())
```

### Output:

``` bash
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 3 entries, 0 to 2
Data columns (total 3 columns):
 #   Column  Non-Null Count  Dtype  
---  ------  --------------  -----  
 0   Name    3 non-null      object 
 1   Age     3 non-null      int64  
 2   Marks   3 non-null      int64
```


---

## 3. Accessing Data

```bash
# Access single column
print(df['Name'])

# Access multiple columns
print(df[['Name', 'Marks']])

# Access specific row (by index)
print(df.iloc[1])  # row 1

# Access using label-based indexing
print(df.loc[0, 'Name'])
```


---

## 4. Adding and Removing Columns

```bash
# Add a new column
df['Grade'] = ['B', 'A', 'A+']

# Delete a column
df.drop('Age', axis=1, inplace=True)

print(df)
``` 

### Output:

``` bash
Name  Marks Grade
0  Ujjawal     85     B
1    Rohan     90     A
2    Priya     95    A+
```


---

## 5. Filtering Data

```bash
# Show students who scored more than 85
print(df[df['Marks'] > 85])
```

### Output:

```bash
Name  Marks Grade
1  Rohan     90     A
2  Priya     95    A+
```


---

## 6. Sorting Data

``` bash
# Sort by marks
print(df.sort_values(by='Marks', ascending=False))
``` 

### Output:

```bash
Name  Marks Grade
2  Priya     95    A+
1  Rohan     90     A
0  Ujjawal   85     B
```


---

## 7. Handling Missing Data

```bash
data = {'Name': ['Ujjawal', 'Rohan', None],
        'Marks': [85, None, 90]}
df2 = pd.DataFrame(data)

# Fill missing values
df2_filled = df2.fillna({'Name': 'Unknown', 'Marks': 0})

print(df2_filled)
```

### Output:

``` bash
Name  Marks
0  Ujjawal   85.0
1    Rohan    0.0
2  Unknown   90.0
```

---

## 8. Grouping Data

``` bash
data = {
    'Department': ['CS', 'IT', 'CS', 'IT'],
    'Marks': [85, 90, 75, 80]
}
df3 = pd.DataFrame(data)

print(df3.groupby('Department')['Marks'].mean())
``` 

## Output:

``` bash
Department
CS    80.0
IT    85.0
Name: Marks, dtype: float64
```


---

## 9. Merging and Joining

```bash
df1 = pd.DataFrame({'ID': [1, 2, 3], 'Name': ['Ujjawal', 'Rohan', 'Priya']})
df2 = pd.DataFrame({'ID': [1, 2, 3], 'Marks': [85, 90, 95]})

merged = pd.merge(df1, df2, on='ID')
print(merged)
```

## Output:

```bash
ID     Name  Marks
0   1  Ujjawal     85
1   2    Rohan     90
2   3    Priya     95
```


---

## 10. Exporting Data

```bash
# Save to Excel
df.to_excel("students.xlsx", index=False)


# Save to JSON
df.to_json("students.json", orient='records')
```
