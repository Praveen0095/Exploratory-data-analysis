# Exploratory Data Analysis (EDA) Project

Welcome to the Exploratory Data Analysis (EDA) project! This repository contains code and documentation for analyzing factors affecting passenger numbers based on airfare rates. The goal of this project is to uncover trends and patterns in the dataset and provide actionable insights.

## Table of Contents
- [Introduction](#introduction)
- [Dataset](#dataset)
- [Setup](#setup)
- [Data Exploration](#data-exploration)
- [Data Cleaning](#data-cleaning)
- [Data Analysis](#data-analysis)
- [Feature Engineering](#feature-engineering)
- [Modeling](#modeling)
- [Conclusion](#conclusion)
- [Future Work](#future-work)
- [Contributing](#contributing)
- [License](#license)

## Introduction
In this project, we perform exploratory data analysis on a dataset containing information about airfare and passenger numbers. The aim is to understand the relationship between these variables and identify key trends and insights.

## Dataset
The dataset used in this project is a CSV file named `Consumer_Airfare_Report_Table.csv`. It contains the following columns:
- `Year`: year of trip.
- `citymaretid`: A unique id of the city
- `city`: The city where the trips has taken.
- `distance`: The distance covered in a trip.
- `cur_fare`: The cost of current airfare.
- `cur_passengers`: The number of current passengers.
- `ly_fare`: The cost of lastyear airfare.
- `ly_passengers`: The number of lastyear passengers.

## Setup
To get started with this project, follow these steps:

1. Clone the repository:
    ```bash
    git clone https://github.com/Praveen0095/Exploratory-data-analysis.git
    cd Exploratory-data-analysis
    ```

2. Install the required Python packages:
    ```bash
    pip install -r requirements.txt
    ```

3. Run the Jupyter Notebook:
    ```bash
    jupyter notebook
    ```

## Data Exploration
We begin by loading the dataset and performing initial exploration to understand its structure and contents. This includes displaying the first few rows, checking for missing values, and summarizing basic statistics.

```python
import pandas as pd

# Load the dataset
da = pd.read_csv('Consumer_Airfare_Report_Table.csv')

# Displaying the columns in the dataframe
da.columns

# Display the first few rows of the dataframe
print(da.head(10))


# Check for missing values
print(df.isnull().sum())
```

# Data Cleaning
As we did our finding on the number of null values/ missing values in this dataframe. We proceeds with the removal of null vales from the dataframe.

```python
# Removal of null values
da.dropna(inplace=True)

# Displaying the sum of null values in the dataframe after the operation of removal
pd.isnull(da).sum()
