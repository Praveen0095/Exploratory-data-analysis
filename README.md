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
- `Geocoded_city`: Geographical code of a city.
- `cur_yield`: Yield achieved in current year.
- `ly_yield`: yield achieved in last year

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
```
Index(['Year', 'quarter', 'citymarketid', 'city', 'markets', 'cur_passengers',
       'cur_fare', 'cur_yield', 'distance', 'ly_passengers', 'ly_fare',
       'ly_yield', 'ly_distance', 'Geocoded_City', 'trip_id'],
      dtype='object') 
      
```python
# Display the first few rows of the dataframe
print(da.head(10))


# Check for missing values
print(df.isnull().sum())
```

| Column         |  Count |
|--------------- |------- |
| Year           |      0 |
| quarter        |      0 |
| citymarketid   |      0 |
| city           |      0 |
| markets        |      0 | 
| cur_passengers |      0 |
| cur_fare       |      0 |
| cur_yield      |      0 |
| distance       |      0 |
| ly_passengers  |      3 |
| ly_fare        |      3 |
| ly_yield       |      3 |
| ly_distance    |      3 |
| Geocoded_City  |   1326 |
| tbl2pk         |      0 |


# Data Cleaning
 ### Removal of NULL values

```python
# Removal of null values
da.dropna(inplace=True)

# Displaying the sum of null values in the dataframe after the operation of removal
pd.isnull(da).sum()

```
| Column         |  count  |
| -------------- | ------- |
| Year           |     0   |
| quarter        |     0   |
| citymarketid   |     0   |
| city           |     0   |
| markets        |     0   |
| cur_passengers |     0   |
| cur_fare       |     0   |
| cur_yield      |     0   |
| distance       |     0   |
| ly_passengers  |     0   |
| ly_fare        |     0   |
| ly_yield       |     0   |
| ly_distance    |     0   |
| Geocoded_City  |     0   |
| tbl2pk         |     0   |

  ### Changing the datatype of a column
```python

#changing a datatypes of an column
# As the distance is measured in Nm. The decimal value can be negligible
# The intial datatype of the distance is float 
# This method helps us to convert the float datasets into integer datasets
da['distance'] = da['distance'].astype('int')


#With the help of dtypes function we can find the datatype of particular column
da['distance'].dtypes

```
   dtype('int32')
   
  ### Changing a  column name
```python 
#Renaming a column
da.rename(columns= {'tbl2pk': 'trip_id'}, inplace=True)

#After the convertion of the datatype
da.info()
```
|  #  |  Column        |     Non-Null Count | Dtype   |  
| --- | ------         |  --------------    | -----   |
|  0  |  Year          |   6699 non-null    | int64   | 
|  1  | quarter        |   6699 non-null    | int64   | 
|  2  | citymarketid   |   6699 non-null    | int64   | 
|  3  | city           |   6699 non-null    | object  | 
|  4  | markets        |   6699 non-null    | int64   | 
|  5  | cur_passengers |   6699 non-null    | int64   |
|  6  | cur_fare       |   6699 non-null    | float64 |
|  7  | cur_yield      |   6699 non-null    | float64 |
|  8  | distance       |   6699 non-null    | int32   |
|  9  | ly_passengers  |   6699 non-null    | float64 |
| 10  | ly_fare        |   6699 non-null    | float64 |
| 11  | ly_yield       |   6699 non-null    | float64 |
| 12  | ly_distance    |   6699 non-null    | float64 |
| 13  | Geocoded_City  |   6699 non-null    | object  |
| 14  | trip_id        |   6699 non-null    | int64   |

##Data Analysis
 ### Description of data
  Description of a data plays a vital role in data analysis this method helps us to find the statstical value (i.e.,, mean, standard deviation, min, max and etc..,)
