# 🏥 Healthcare Data Analysis & Data Cleaning

## 📌 Project Overview

This project focuses on **data cleaning, preprocessing, and exploratory analysis of healthcare data using Python**.

The notebook works with healthcare records containing information such as admission details, medical conditions, medical codes, billing amounts, patient age, admission type, and hospital stay duration.

The main purpose of this project is to clean the raw healthcare dataset and perform basic analysis to understand the patterns within the data.

## 🎯 Objectives

The main objectives of this project are:

* Load and inspect the healthcare dataset.
* Understand the structure and columns of the dataset.
* Identify missing values.
* Handle missing medical codes.
* Convert date columns into the appropriate datetime format.
* Clean admission type values.
* Calculate hospital stay duration.
* Perform descriptive statistical analysis.
* Analyze medical conditions.
* Analyze admission types.
* Compare admission types with medical conditions.
* Calculate average age for different medical conditions.

## 🛠️ Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Jupyter Notebook

## 📂 Dataset

The notebook uses a healthcare dataset named:

```text
healthcare_raw - healthcare_raw.csv
```

The dataset contains healthcare-related patient and hospital information.

### Important Columns

The analysis uses columns including:

| Column              | Description                                          |
| ------------------- | ---------------------------------------------------- |
| `Medical_Code`      | Medical code associated with the healthcare record   |
| `Admission_Date`    | Date on which the patient was admitted               |
| `Discharge_Date`    | Date on which the patient was discharged             |
| `Admission_Type`    | Type of hospital admission                           |
| `Hos_Stay_Days`     | Number of days spent in the hospital                 |
| `Billing_Amount`    | Billing amount associated with the healthcare record |
| `Medical_Condition` | Medical condition associated with the patient        |
| `Age`               | Patient's age                                        |

## 🔍 Data Analysis Process

### 1. Importing Libraries

The project imports the following Python libraries:

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

### 2. Loading the Dataset

The healthcare dataset is loaded using Pandas:

```python
df = pd.read_csv("healthcare_raw - healthcare_raw.csv")
```

The first few records are displayed using:

```python
df.head()
```

### 3. Dataset Inspection

The notebook examines the dataset using:

```python
df.shape
df.columns
df.info()
```

This helps understand:

* Number of records
* Number of columns
* Column names
* Data types
* Dataset structure

## 🧹 Data Cleaning

### Missing Value Analysis

Missing values are checked using:

```python
df.isnull()
df.isnull().sum()
```

The notebook specifically checks missing values in the `Medical_Code` column.

### Handling Missing Medical Codes

Missing values in `Medical_Code` are replaced with:

```text
Unknown
```

using:

```python
df['Medical_Code'] = df['Medical_Code'].fillna('Unknown')
```

The column is then checked again to verify the missing values have been handled.

## 📅 Date Conversion

The following columns are converted into datetime format:

* `Admission_Date`
* `Discharge_Date`

```python
df['Admission_Date'] = pd.to_datetime(df['Admission_Date'])
df['Discharge_Date'] = pd.to_datetime(df['Discharge_Date'])
```

The data types are then verified.

## 🏥 Admission Type Cleaning

The `Admission_Type` column is cleaned by:

* Removing unnecessary spaces.
* Converting values to lowercase.

```python
df['Admission_Type'] = (
    df['Admission_Type']
    .str.strip()
    .str.lower()
)
```

This helps maintain consistent values for further analysis.

## 🛏️ Hospital Stay Calculation

A new column called `Hos_Stay_Days` is created.

It calculates the number of days between admission and discharge:

```python
df["Hos_Stay_Days"] = (
    df['Discharge_Date'] - df['Admission_Date']
).dt.days
```

This allows the project to analyze the duration of hospital stays.

## 📊 Statistical Analysis

### Billing Amount

Descriptive statistics are calculated for `Billing_Amount`:

```python
df['Billing_Amount'].describe()
```

This provides statistical information about healthcare billing amounts.

### Hospital Stay

Statistical information for hospital stay duration is calculated using:

```python
df['Hos_Stay_Days'].describe()
```

This helps understand the distribution of hospital stay durations.

## 🩺 Medical Condition Analysis

The notebook analyzes the frequency of different medical conditions using:

```python
df["Medical_Condition"].value_counts()
```

This identifies how frequently each medical condition appears in the dataset.

## 🏥 Admission Type Analysis

The project analyzes the distribution of admission types using:

```python
df['Admission_Type'].value_counts()
```

This provides the number of records associated with each admission type.

## 🔄 Admission Type vs Medical Condition

A cross-tabulation is created between:

* `Admission_Type`
* `Medical_Condition`

using:

```python
pd.crosstab(
    df['Admission_Type'],
    df['Medical_Condition']
)
```

This helps examine the relationship between admission types and medical conditions.

## 👥 Average Age by Medical Condition

The notebook calculates the average patient age for each medical condition:

```python
df.groupby('Medical_Condition')['Age'].mean()
```

This provides an overview of the average age associated with each medical condition.

## 📌 Key Analysis Areas

The project covers:

* Dataset structure
* Missing-value handling
* Data type conversion
* Text cleaning
* Feature creation
* Billing statistics
* Hospital stay analysis
* Medical condition frequency
* Admission type distribution
* Admission type and medical condition comparison
* Average age by medical condition

## 📁 Project Structure

```text
Healthcare-Data-Analysis/
│
├── healthcare_analysis.ipynb
├── healthcare_raw.csv
└── README.md
```

## 🚀 How to Run the Project

### Step 1: Install Required Libraries

```bash
pip install numpy pandas matplotlib seaborn jupyter
```

### Step 2: Open Jupyter Notebook

```bash
jupyter notebook
```

### Step 3: Open the Notebook

Open the healthcare analysis `.ipynb` file.

### Step 4: Add the Dataset

Keep the healthcare CSV dataset in the appropriate project directory and update the file path if required.

### Step 5: Run the Notebook

Run the cells sequentially to perform the complete data cleaning and analysis process.

## 🎓 Skills Demonstrated

This project demonstrates practical knowledge of:

* Python Programming
* Pandas
* NumPy
* Data Cleaning
* Data Preprocessing
* Missing Value Handling
* Datetime Conversion
* Feature Engineering
* Descriptive Statistics
* Data Analysis
* Cross-tabulation
* GroupBy Analysis
* Jupyter Notebook

## 👩‍💻 Author

**Madhumidha**
