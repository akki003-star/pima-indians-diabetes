# pima-indians-diabetes
# 🩺 Pima Indians Diabetes — Data Analysis & Visualization

## 📌 Project Overview

This project performs an end-to-end **Data Analysis, Data Cleaning, Exploratory Data Analysis (EDA), and Data Visualization** workflow using the **Pima Indians Diabetes dataset**.

The main objective is to identify data-quality issues, clean the dataset, explore relationships between patient characteristics and diabetes outcomes, and communicate important patterns through professional visualizations.

The project was developed using **Python, Pandas, NumPy, Matplotlib, Seaborn, and Google Colab**.

---

## 🎯 Objectives

* Understand the structure and quality of the dataset
* Identify missing values and invalid values
* Handle zero values that represent missing measurements
* Check and handle duplicate records
* Detect statistical outliers using the IQR method
* Perform exploratory data analysis
* Analyze relationships between features and diabetes outcome
* Create meaningful and insight-focused visualizations
* Prepare a clean dataset for further analysis
* Document the complete analysis in a reproducible Jupyter/Colab notebook

---

## 📊 Dataset

The dataset contains information about female patients of Pima Indian heritage and a binary diabetes outcome.

### Features

| Feature                    | Description                       |
| -------------------------- | --------------------------------- |
| `Pregnancies`              | Number of pregnancies             |
| `Glucose`                  | Plasma glucose concentration      |
| `BloodPressure`            | Diastolic blood pressure          |
| `SkinThickness`            | Triceps skin fold thickness       |
| `Insulin`                  | 2-hour serum insulin              |
| `BMI`                      | Body Mass Index                   |
| `DiabetesPedigreeFunction` | Diabetes pedigree function        |
| `Age`                      | Age of the patient                |
| `Outcome`                  | Diabetes outcome: 0 = No, 1 = Yes |

### Target Variable

`Outcome`

```text
0 → No diabetes
1 → Diabetes
```

---

## 🔍 Data Quality Assessment

The initial dataset was examined using:

* `head()`
* `shape`
* `info()`
* `describe()`
* `isnull().sum()`
* Duplicate detection
* Zero-value analysis
* IQR-based outlier detection

### Issues Identified

#### 1. Missing Values

The original dataset does not contain conventional `NaN` values in several measurement columns. However, some measurements contain `0`, which is not physiologically meaningful for those variables.

The following columns were investigated:

```python
Glucose
BloodPressure
SkinThickness
Insulin
BMI
```

#### 2. Zero Values

Zero values in the above measurement columns were treated as missing values.

```python
df[missing_columns] = df[missing_columns].replace(0, np.nan)
```

`Pregnancies` and `Outcome` were not modified because zero is a valid value for those fields.

#### 3. Missing Value Treatment

After converting invalid zero values to `NaN`, missing numeric values were replaced using the **median**.

```python
for column in missing_columns:
    df[column] = df[column].fillna(df[column].median())
```

Median imputation was selected because it is less sensitive to extreme values than mean imputation.

#### 4. Duplicate Records

Duplicate records were checked using:

```python
df.duplicated().sum()
```

Duplicate records were removed only if present.

#### 5. Outliers

Statistical outliers were identified using the **Interquartile Range (IQR)** method.

```text
IQR = Q3 - Q1

Lower Limit = Q1 - 1.5 × IQR
Upper Limit = Q3 + 1.5 × IQR
```

Outliers were **not automatically deleted** because an extreme statistical observation is not necessarily an incorrect record.

---

## 🧹 Data Cleaning Workflow

The project follows this workflow:

```text
Raw Dataset
     ↓
Load Dataset
     ↓
Assign Column Names
     ↓
Understand Dataset
     ↓
Check Data Types
     ↓
Check Missing Values
     ↓
Check Zero Values
     ↓
Convert Invalid Zeros → NaN
     ↓
Median Imputation
     ↓
Check Duplicates
     ↓
Detect Outliers
     ↓
Clean Dataset
     ↓
Exploratory Data Analysis
     ↓
Visualization
     ↓
Key Insights
```

---

## 📈 Exploratory Data Analysis

The following questions were investigated:

### 1. How is the diabetes outcome distributed?

The distribution of `Outcome = 0` and `Outcome = 1` was analyzed to understand the target variable.

### 2. Does glucose differ between outcome groups?

Glucose distributions were compared between patients with:

```text
Outcome = 0
Outcome = 1
```

### 3. Does BMI differ between outcome groups?

BMI distributions were analyzed using descriptive statistics and boxplots.

### 4. Does age differ between outcome groups?

Age distributions were compared across the two outcome groups.

### 5. Which variables have stronger relationships with the outcome?

A correlation matrix was created to examine linear relationships between numerical features.

---

## 📊 Visualizations

The project contains five major visualizations.

### 1. Diabetes Outcome Distribution

A bar chart showing the number of patients in each outcome category.

### 2. Glucose Distribution by Outcome

A boxplot comparing glucose distributions between the two outcome groups.

### 3. Diabetes Outcome Rate by Glucose Category

Glucose values were grouped into categories and the percentage of `Outcome = 1` was calculated for each category.

This visualization provides a more meaningful comparison than simply plotting individual glucose values.

### 4. BMI Distribution by Outcome

A boxplot showing BMI differences between the two outcome groups.

### 5. Correlation Matrix

A heatmap showing correlations among the numerical variables.

---

## 💡 Key Findings

The analysis shows several notable patterns:

* Higher glucose categories have a higher proportion of `Outcome = 1` in this dataset.
* Older age groups generally show higher outcome rates than younger groups.
* BMI distributions differ between the two outcome groups, although there is considerable overlap.
* Glucose has one of the strongest linear associations with the diabetes outcome among the numerical variables.
* The dataset contains statistical outliers, but these were retained because they may represent legitimate observations.

> **Note:** These findings represent associations observed in this dataset. They should not be interpreted as evidence of causation or as medical diagnosis.

---

## 🛠️ Technologies Used

### Programming Language

* Python

### Libraries

* Pandas
* NumPy
* Matplotlib
* Seaborn

### Development Environment

* Google Colab
* Jupyter Notebook

### Version Control

* Git
* GitHub

---

## 📁 Project Structure

```text
pima-diabetes-data-analysis/
│
├── Pima_Diabetes_Data_Analysis.ipynb
│
├── pima-indians-diabetes.csv
│
├── pima_diabetes_cleaned.csv
│
├── visualizations/
│   ├── outcome_distribution.png
│   ├── glucose_vs_outcome.png
│   ├── glucose_category_outcome_rate.png
│   ├── bmi_vs_outcome.png
│   └── correlation_heatmap.png
│
└── README.md
```

---

## 🚀 How to Run the Project

### Option 1 — Google Colab

Open the notebook in Google Colab and upload the dataset.

Run the notebook cells sequentially from beginning to end.

### Option 2 — Local Jupyter Notebook

Clone the repository:

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
```

Navigate to the project:

```bash
cd pima-diabetes-data-analysis
```

Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open:

```text
Pima_Diabetes_Data_Analysis.ipynb
```

---

## 📌 Skills Demonstrated

This project demonstrates practical skills in:

* Data Cleaning
* Data Validation
* Missing Value Handling
* Data Imputation
* Duplicate Detection
* Outlier Detection
* Exploratory Data Analysis
* Descriptive Statistics
* GroupBy Analysis
* Correlation Analysis
* Data Visualization
* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Google Colab
* Git & GitHub

---

## 👨‍💻 Project Outcome

This project demonstrates an end-to-end approach to transforming a raw dataset into a clean, analyzed, and visually communicated dataset.

The workflow emphasizes **data quality, reproducibility, analytical reasoning, and clear communication of insights**, which are important skills for an entry-level **Data Analyst** role.

---

## ⚠️ Disclaimer

This project is intended for **educational and data-analysis purposes only**. The analysis describes patterns in the dataset and should not be used for medical diagnosis or clinical decision-making.
