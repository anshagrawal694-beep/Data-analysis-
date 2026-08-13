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
