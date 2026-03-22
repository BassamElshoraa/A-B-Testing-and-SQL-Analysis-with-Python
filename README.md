# A/B Testing and SQL Analysis with Python

## Overview

A/B testing is one of the most effective ways to evaluate whether a product or marketing change truly improves performance. However, observing a difference in metrics is not enough on its own — statistical testing is required to determine whether the difference is meaningful or simply due to random variation.

This project delivers a complete **Python-based A/B testing analysis** that combines **data cleaning**, **SQL querying**, and **statistical hypothesis testing** to compare the performance of **Test** and **Control** groups based on **Click-Through Rate (CTR)** for a specific banner campaign.

The workflow uses **Pandas** for data preparation, **SQLite with SQLAlchemy** for structured querying, and **SciPy** for statistical testing, followed by visualizations to communicate the findings clearly.

---

## Tools & Technologies Used

- **Python 3**
- **Jupyter Notebook**
- **Pandas**: For loading, cleaning, and manipulating the datasets
- **SQLite**: For SQL-based analysis using an in-memory database
- **SQLAlchemy**: For database connection and SQL execution
- **SciPy**: For statistical significance testing
- **Matplotlib**: For data visualization

---

## Dataset Overview

The analysis uses three input files:

- **`test_customer_keys.csv`**  
  Contains customer keys and identifies whether each customer belongs to the Test group.

- **`banner_views.csv`**  
  Contains banner impression records, including customer key, banner name, and timestamp.

- **`banner_clicks.csv`**  
  Contains banner click records, including customer key, banner name, and timestamp.

The target of the analysis is the **`Juhayna60`** banner.

---

## Project Workflow

### 1. Data Loading
The notebook loads the three CSV datasets into Pandas DataFrames for preprocessing and analysis.

### 2. Data Cleaning
The analysis checks for missing values in all datasets and removes incomplete rows where necessary to ensure cleaner downstream analysis.

### 3. SQLite Database Creation
An in-memory SQLite database is created, and all cleaned DataFrames are loaded into SQL tables.

### 4. Customer Group Assignment
A SQL view named **`customer_groups`** is created to assign each customer into either:

- **Test**
- **Control**

based on whether the customer key exists in the `test_customer_keys` table.

### 5. Impressions and Clicks Analysis
A SQL query is used to calculate the total number of:

- **Impressions**
- **Clicks**

for the **Juhayna60** banner across both groups.

### 6. CTR Calculation
Click-Through Rate (CTR) is calculated using:

```python
CTR = (clicks / impressions) * 100
