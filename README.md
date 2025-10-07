# Pandas
 Pandas
# 🧠 Introduction to Pandas

Pandas is one of the most useful libraries in Python for data handling and analysis.
It helps you organize and study data just like you would in Excel or a database table — but with much more speed and flexibility.

## 💡 Why use Pandas?

You can easily read, modify, and save data from CSV, Excel, or JSON files.

It makes data cleaning and analysis very simple.

It works well with other libraries like NumPy, Matplotlib, and Scikit-learn.

👉 To start using it:

import pandas as pd

# 📊 Main Data Structures in Pandas

Pandas provides two main data containers:

## 1️⃣ Series – Single Column Data

A Series is like a list with labels.
It stores one-dimensional data with an index attached to each value.

### Example:
import pandas as pd

scores = pd.Series([55, 60, 72, 88], index=['A', 'B', 'C', 'D'])
print(scores)

### Output:
A    55
B    60
C    72
D    88
dtype: int64


Here each value (55, 60, 72, 88) has a label (A, B, C, D).
You can think of it like a dictionary where labels are keys.

## 2️⃣ DataFrame – Table with Rows and Columns

A DataFrame is a 2D table, similar to an Excel sheet.
It can store multiple columns of different data types.

### Example:
students = {
    'Student': ['Arjun', 'Meera', 'Kabir', 'Simran'],
    'Age': [18, 19, 18, 20],
    'Score': [82, 90, 75, 88]
}

df = pd.DataFrame(students)
print(df)

### Output:
  Student  Age  Score
0   Arjun   18     82
1   Meera   19     90
2   Kabir   18     75
3  Simran   20     88


👉 Each column is actually a Series combined together.

## 📁 Reading and Writing Data
### 🔹 Reading Data:
data = pd.read_csv("students.csv")  # Read CSV file

### 🔹 Writing Data:
df.to_csv("result.csv", index=False)  # Save DataFrame to file


Pandas supports many formats — like Excel (.xlsx), JSON, and SQL databases.

## 🧩 Exploring the Data
### View first or last few records
df.head()   # First 5 rows
df.tail(3)  # Last 3 rows

### Get info about the dataset
df.info()
df.describe()


These give details like data types, missing values, and summary statistics.

## 🔍 Accessing and Selecting Data
### Selecting Columns
df['Student']         # Single column
df[['Student', 'Score']]  # Multiple columns

### Selecting Rows
df.iloc[2]            # Row by index number
df.loc[1, 'Score']    # Specific value using label

### Example Output:
75

## 🧮 Adding, Updating, and Deleting Data
### Add new column
df['Grade'] = ['B', 'A+', 'C', 'A']

### Update column
df['Score'] = df['Score'] + 5  # Adding 5 marks to all students

### Remove a column
df.drop('Age', axis=1, inplace=True)

### Output:
  Student  Score Grade
0   Arjun     87     B
1   Meera     95    A+
2   Kabir     80     C
3  Simran     93     A

# 🔦 Filtering and Sorting
### Filter rows based on condition
high_scorers = df[df['Score'] > 85]
print(high_scorers)

### Sort the DataFrame
df.sort_values(by='Score', ascending=False)

### Output:
  Student  Score Grade
1   Meera     95    A+
3  Simran     93     A
0   Arjun     87     B
2   Kabir     80     C

# 🧹 Handling Missing or Incomplete Data
data = {
    'Name': ['Amit', None, 'Riya'],
    'Marks': [90, None, 78]
}

df2 = pd.DataFrame(data)

### Fill missing data
df2.fillna({'Name': 'Unknown', 'Marks': 0}, inplace=True)

### Output:
     Name  Marks
0    Amit   90.0
1  Unknown    0.0
2    Riya   78.0

# 🔗 Combining DataFrames
### Merging Data
info = pd.DataFrame({'Roll': [1, 2, 3], 'Name': ['Amit', 'Riya', 'Karan']})
marks = pd.DataFrame({'Roll': [1, 2, 3], 'Score': [85, 90, 88]})

merged = pd.merge(info, marks, on='Roll')
print(merged)

### Output:
   Roll   Name  Score
0     1   Amit     85
1     2   Riya     90
2     3  Karan     88

## 📊 Grouping and Aggregation

### Grouping helps summarize large datasets.

#### Example:
data = {
    'Department': ['CS', 'CS', 'IT', 'IT', 'IT'],
    'Marks': [85, 78, 92, 80, 75]
}

df3 = pd.DataFrame(data)
avg_marks = df3.groupby('Department')['Marks'].mean()
print(avg_marks)

#### Output:
Department
CS    81.5
IT    82.3
Name: Marks, dtype: float64

## 💾 Exporting Data to Other Formats
df.to_excel("student_data.xlsx", index=False)
df.to_json("student_data.json", orient='records')

🌟 Summary
