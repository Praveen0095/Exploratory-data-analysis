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

# Data Analysis
 ### Description of data and Value count
  Description of a data and value count plays a vital role in data analysis.describe() method helps us to find the statstical value (i.e.,, mean, standard deviation, min, max and etc..,) and value_count() help us to find the number of repeatation in datasets

  ```python
   #describe() method helps us to find the description of the data in dataframe(i.e count, mean, std, etc..,)
    da['distance'].describe()

  ```
  | Description      |   value       |
  | ----- |  ------------ |
  | count |   6699.000000 |
  | mean  |    955.198388 |
  | std   |    196.314161 |
  | min   |    334.000000 |
  | 25%   |    845.500000 |
  | 50%   |    960.000000 |
  | 75%   |   1081.000000 |
  | max   |   1500.000000 |
  | Name: distance | dtype: float64 |

  
  ```python
  #value_count() method helps us to find the total number of repeatation in a particular dataset
   city_count=da['city'].value_counts()
   print(city_count)

  ```
 | city                               |             |
 | -----                              |--------     |
 | Salt Lake City, UT                 |       94    |
 | Washington, DC (Metropolitan Area) |       94    |
 | Dallas/Fort Worth, TX              |       94    |
 | Minneapolis/St. Paul, MN           |       94    |
 | Miami, FL (Metropolitan Area)      |       94    |
 |                                    |       ..    |
 | Wichita, KS                        |       1     |
 | Bozeman, MT                        |       1     |
 | Tallahassee, FL                    |       1     |
 | Pensacola, FL                      |       1     |
 | Everett, WA                        |       1     |
 |Name: count, Length: 91, dtype: int64 |

### Analysis based on Fares
   To analyse the data based on the airfare we need the following dataset from the dataframe
   `ly-fare`: The cost of last year airfare
   `cur_fare`: The cost of current year airfare

   As the datframe has more than 90 city. We proceed by selecting Four random city from the datframe for easy computation and Handling .The randomly selected city are 
   
   `New Orleans, LA`
   `Miami, FL (Metropolitan Area)`
   `Washington, DC (Metropolitan Area)`
   `Los Angeles, CA (Metropolitan Area)`

   ```python
       # Assigning variables for city
       city_name1 = 'New Orleans, LA'
       city_name2 = 'Miami, FL (Metropolitan Area)'
       city_name3 = 'Washington, DC (Metropolitan Area)'
       city_name4 = 'Los Angeles, CA (Metropolitan Area)'
   ```

   After assigning variables for the cities. We have to filter out the Airfare(Lastyear and Currentyear) for the selected ciies.
   
   ```python
        #Filtering current fare from the dataframe frame for the chosen city
        city_fares1 = da[da['city'] == city_name1]['cur_fare']
        city_fares2 = da[da['city'] == city_name2]['cur_fare']
        city_fares3 = da[da['city'] == city_name3]['cur_fare']
        city_fares4 = da[da['city'] == city_name4]['cur_fare']


       # Filtering last year fare from the dataframe frame for the chosen city
        city_fares1_ly= da[da['city'] == city_name1]['ly_fare']
        city_fares2_ly= da[da['city'] == city_name2]['ly_fare']
        city_fares3_ly= da[da['city'] == city_name3]['ly_fare']
        city_fares4_ly= da[da['city'] == city_name4]['ly_fare']

   ```
   After filtering out the data we then proceed with finding the mean of the airfare.

   ```python
      # Calculate the mean fare for the chosen city
        mean_cur_fare1= city_fares1.mean()
        mean_cur_fare2= city_fares2.mean()
        mean_cur_fare3= city_fares3.mean()
        mean_cur_fare4= city_fares4.mean()

      #Caluculation of mean fare for the chosen city for last year
        mean_ly_fare1= city_fares1_ly.mean()
        mean_ly_fare2= city_fares2_ly.mean()
        mean_ly_fare3= city_fares3_ly.mean()
        mean_ly_fare4= city_fares4_ly.mean()

     #storing the calculated values in the form of dictionary
       cur_faretable = {'City': [city_name1,city_name2,city_name3,city_name4], 'Mean': [mean_cur_fare1,mean_cur_fare2,mean_cur_fare3,mean_cur_fare4],'Type':['Current Fare'] * 4}
       ly_faretable = {'City': [city_name1,city_name2,city_name3,city_name4], 'Mean': [mean_ly_fare1,mean_ly_fare1,mean_ly_fare3,mean_ly_fare4],'Type':['Lastyear Fare'] * 4}
       print(cur_faretable)
       print(ly_faretable)
   ```
  
   ```text
      {'City': ['New Orleans, LA', 'Miami, FL (Metropolitan Area)', 'Washington, DC (Metropolitan Area)', 'Los Angeles, CA (Metropolitan Area)'], 'Mean': [171.97744680851062, 170.27712765957446, 193.91765957446808, 190.49563829787235], 'Type': ['Current Fare', 'Current Fare', 'Current Fare', 'Current Fare']}
      {'City': ['New Orleans, LA', 'Miami, FL (Metropolitan Area)', 'Washington, DC (Metropolitan Area)', 'Los Angeles, CA (Metropolitan Area)'], 'Mean': [170.49170212765958, 170.49170212765958, 193.35659574468082, 189.38212765957448], 'Type': ['Lastyear Fare', 'Lastyear Fare', 'Lastyear Fare', 'Lastyear Fare']}
   ```
