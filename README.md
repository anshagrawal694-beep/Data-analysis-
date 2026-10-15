# Data-analysis-
Diabetes data analysis.

## Project Overview

This notebook performs an exploratory data analysis (EDA) on the `diabetes.csv` dataset. The goal is to understand the dataset's characteristics, clean the data by handling missing or invalid values, and visualize key distributions and relationships.

## Analysis Steps

1.  **Data Loading and Initial Inspection**: The `diabetes.csv` dataset was loaded into a pandas DataFrame. Initial checks included viewing the head and tail of the DataFrame, checking its shape, column names, and data types using `df.head()`, `df.tail()`, `df.shape`, `df.columns`, and `df.dtypes`.

2.  **Descriptive Statistics**: A statistical summary of the dataset was generated using `df.describe()` to understand the central tendency, dispersion, and shape of the distribution of the dataset’s numerical columns.

3.  **Missing Values and Duplicates**: The presence of null values was checked using `df.isnull().count()` and duplicate rows were identified using `df.duplicated().sum()`. The `nunique()` function was used to determine the number of unique values in each column.

4.  **Data Filtering and Selection**: Data was filtered based on various conditions, such as `Age > 67` and combinations of `Age` and `Outcome`, as well as `Glucose` and `BMI`. Specific rows were selected using `iloc`.

5.  **Sorting and Grouping**: The DataFrame was sorted by single columns like `Age` and `Glucose`, and by multiple columns (`Age` and `Glucose`). Value counts for `Age` were also calculated and displayed.

6.  **Descriptive Statistics (Advanced)**: Mean, median, and standard deviation for various columns (e.g., `BMI`, `Age`) were calculated, and the correlation matrix for all numerical features was computed using `df.corr()`.

7.  **Feature Engineering**: New categorical features `BMI_CATEGORY` and `Glucose_Level` were created based on existing numerical columns `BMI` and `Glucose`, respectively.

8.  **Data Cleaning - Handling Zero Values**: Invalid zero values in 'Glucose', 'BloodPressure', and 'Insulin' columns were replaced with the mean of their respective columns to ensure more accurate analysis and model training.

9.  **Data Visualization**: A histogram of the 'Age' distribution was generated using `matplotlib.pyplot` to visually inspect the age demographics within the dataset.


FOR DATAlOADINGSTORAGE 

# Data Loading and Data Storage with Pandas

A beginner-friendly Python notebook covering how to create, read,
inspect, and store tabular data using **Pandas** and Python file
handling.

## 📌 Overview

This project demonstrates a basic data workflow:

**Data source → Load data → Pandas DataFrame → Store data**

The examples use a small student dataset containing student names, roll
numbers, marks, and attendance.

## 🎯 What You'll Learn

-   Import `pandas` and `os`
-   Check the current working directory and list files
-   Create a Pandas DataFrame
-   Save a DataFrame to a CSV file
-   Open, read, append to, and close a file with Python
-   Load CSV data with `pd.read_csv()`
-   Inspect a DataFrame using `shape`, `dtypes`, and `head()`
-   Use common CSV-reading parameters:
    -   `sep`
    -   `header`
    -   `names`
    -   `index_col`
    -   `usecols`
    -   `nrows`
    -   `skiprows`

## 🧰 Requirements

-   Python 3
-   Jupyter Notebook or Google Colab
-   Pandas

Install Pandas if it is not already installed:

``` bash
pip install pandas
```

## 🚀 Getting Started

1.  Clone or download this repository.
2.  Open `DataLoadingStorage.ipynb` in Jupyter Notebook or Google Colab.
3.  Run the cells from top to bottom.

You can also open the notebook in Google Colab using the link provided
at the top of the notebook.

## 📂 Example Dataset

The notebook uses this student dataset:

  student_name     roll_no   marks attendance
  -------------- --------- ------- ------------
  A                    101      85 Present
  B                    102      72 Absent
  C                    103      91 Present
  D                    104      68 Present
  E                    105      88 Present

## 💻 Examples

### 1. Import libraries

``` python
import pandas as pd
import os
```

### 2. Check the working directory

``` python
print(os.getcwd())       # Show the current working directory
print(os.listdir())      # List files in the current directory
```

The working directory is where Python looks for relative file paths and
where it saves output files by default.

### 3. Create a DataFrame and save it as CSV

``` python
df = pd.DataFrame({
    "student_name": ["A", "B", "C", "D"],
    "roll_no": [101, 102, 103, 104],
    "marks": [85, 72, 91, 68],
    "attendance": ["Present", "Absent", "Present", "Present"]
})

df.to_csv("StudentsData.csv", index=False)
```

`index=False` prevents Pandas from writing the DataFrame's index as an
extra CSV column.

### 4. Read a file using Python file handling

``` python
with open("StudentsData.csv", "r", encoding="utf-8") as f:
    print(f.read())
```

Using `with open(...)` closes the file automatically after the block
finishes.

### 5. Append a row to a CSV file

``` python
with open("StudentsData.csv", "a", encoding="utf-8") as f:
    f.write("E,105,88,Present\n")
```

Use append mode (`"a"`) to add data to the end of a file. The newline
`\n` keeps the new record on a separate line. Only append a row if it is
not already present.

### 6. Load the CSV into a DataFrame

``` python
df = pd.read_csv("StudentsData.csv")
print(df)
```

### 7. Inspect the DataFrame

``` python
print(df.shape)    # Number of rows and columns
print(df.dtypes)   # Data type of each column
print(df.head())   # First five rows
print(df.head(3))  # First three rows
```

Remember to call `head()` with parentheses. `df.head` refers to the
method; `df.head()` executes it.

## 🔍 Important `read_csv()` Parameters

### `sep`

Defines the delimiter separating values. CSV files normally use a comma.

``` python
df = pd.read_csv("StudentsData.csv", sep=",")
```

For a tab-separated file, use `sep="\t"`.

### `header`

Specifies which row contains column names. `header=0` uses the first row
as the header.

``` python
df = pd.read_csv("StudentsData.csv", header=0)
```

### `names`

Provides custom column names.

``` python
df = pd.read_csv(
    "StudentsData.csv",
    names=["Name", "Roll", "Marks", "Attendance"],
    header=0
)
```

Here, `header=0` tells Pandas to use the first row as the existing
header and replace it with the supplied names.

### `index_col`

Uses a column as the DataFrame index.

``` python
df = pd.read_csv("StudentsData.csv", index_col="roll_no")
```

### `usecols`

Loads only selected columns.

``` python
df = pd.read_csv(
    "StudentsData.csv",
    usecols=["student_name", "marks"]
)
```

### `nrows`

Loads only the specified number of data rows.

``` python
df = pd.read_csv("StudentsData.csv", nrows=3)
```

### `skiprows`

Skips specified row numbers. Row numbering starts at `0`.

``` python
df = pd.read_csv("StudentsData.csv", skiprows=[2, 3])
```

Be careful: skipping row `0` skips the header too, unless you handle the
column names separately.

## 💾 Saving Data Correctly

Use the method that matches the file format:

``` python
df.to_csv("StudentsData.csv", index=False)       # CSV
df.to_excel("StudentsData.xlsx", index=False)    # Excel
df.to_json("StudentsData.json", orient="records", indent=2)  # JSON
df.to_html("StudentsData.html", index=False)     # HTML table
```

**Important:** Changing the filename extension in `to_csv()` does not
convert the file to Excel, JSON, HTML, or XML. Use the appropriate
Pandas export method for each format. Excel export may require
`openpyxl`:

``` bash
pip install openpyxl
```

## 📁 Files

-   `DataLoadingStorage.ipynb` --- notebook containing the examples and
    exercises.
-   `README.md` --- project overview and usage instructions.
-   `StudentsData.csv` --- generated when the notebook runs the CSV
    creation cell.

Generated data files may not be present in the repository until you run
the notebook and save them.

## 🧠 Key Takeaways

-   A **DataFrame** stores tabular data in rows and columns.
-   `pd.read_csv()` loads CSV data into a DataFrame.
-   `to_csv()` exports a DataFrame to CSV.
-   Python's `open()` supports file modes such as `"r"` (read), `"w"`
    (write/overwrite), and `"a"` (append).
-   `shape`, `dtypes`, and `head()` help inspect data.
-   `read_csv()` parameters let you control how a file is parsed and
    which data is loaded.

## 📚 Topics

`Python` · `Pandas` · `Data Analysis` · `CSV` · `File Handling` ·
`Jupyter Notebook`

## 👤 Author

**Ansh Agrawal**

------------------------------------------------------------------------

This is a learning project for practicing basic data loading and storage
operations with Pandas.

