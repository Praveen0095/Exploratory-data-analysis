# Exploratory Data Analysis (EDA) Project

Welcome to the Exploratory Data Analysis (EDA) project! This repository contains code and documentation for analyzing factors affecting passenger numbers based on airfare rates. The goal of this project is to uncover trends and patterns in the dataset and provide actionable insights.

## Table of Contents
- [Introduction](#introduction)
- [Dataset](#dataset)
- [Setup](#setup)
- [Data Exploration](#data-exploration)
- [Data Cleaning](#data-cleaning)
- [Data Analysis](#data-analysis)
- [Conclusion](#conclusion)
- [Future Work](#future-work)
- [Contribution](#contribution)


## Introduction
In this project, we perform exploratory data analysis on a dataset containing information about airfare and passenger numbers. The aim is to understand the relationship between these variables and identify key trends and insights.

 <img src="https://github.com/user-attachments/assets/5c2df556-cd4a-4124-a172-533a31a74960"  width="1366" height="600">


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
  We used dictionary to store our values based on columns(city,mean).We calculated mean of airfare for current year and last year of a city to compare and to determine whether there is changes between them.
  The stored dictionaries is then converted to dataframe for to plot in the graph using matplotlib and seaborn module.

  ```python
      import matplotlib.pyplot as plt
      import seaborn as sns

     #converting the dictionaries to dataframes
     df1=pd.DataFrame(ly_faretable)
     df2=pd.DataFrame(cur_faretable)
     df = pd.concat([df1, df2])

     # Plotting the combined bar graph
     plt.figure(figsize=(15, 7))

    # Plot the  bar plot
    dx=sns.barplot(x='City', y='Mean', hue='Type', data=df)

    # Adding title and labels
    plt.title('Comparison of Fares by City')
    plt.xlabel('City')
    plt.ylabel('Fare')
    for bars in dx.containers:
      dx.bar_label(bars)
  ```
  <img src="https://github.com/user-attachments/assets/9190f716-5e32-4bf1-acc6-e8cab93d8c74" width="1000" height="1000">

  From the above graph, We can draw that the mean of currentyear airfare has increased nearly by 1% than the lastyear airfare.As this information is not sufficent to draw the conclusion so we proceed with comparing the number of passengers on lastyear and currentyear.

  We proceed with the same method we followed to obtain the mean of airfare.

  ```python
     ds1=pd.DataFrame(ly_passenger)
     ds2=pd.DataFrame(cur_passenger)
     ds = pd.concat([ds1, ds2])

     # Plotting the combined bar graph
     plt.figure(figsize=(15, 6))

     # Plot the  bar plot
     ex=sns.barplot(x='City', y='Mean', hue='Type', data=ds)

     # Adding title and labels
     plt.title('Comparison of Passengers by City')
     plt.xlabel('City')
     plt.ylabel('Passengers')
     for bars in ex.containers:
       ex.bar_label(bars)
  ```
<img src="https://github.com/user-attachments/assets/4371ddcc-7d95-4e42-b5aa-1fbdf96a88c1" width="1200" height="1200">

From the above graph we can say that the number of passengers on current year has significantly increased on comparing with the last year passengers.As this grapgh also doesnt give us any clue about the relation between the passengers and airfare.

In order to get more precise result we Select a city from the dataset city which is " New orelans " and we compare the airfare and passengers count based on different years such as(2007,2008,2009).To prove whether there is any relation between the airfare and passengers count 

```python
   #Filtering out the sum of Passengers for the particular year
   Passenger_cur1 = da[(da['Year'] == 2007) & (da['city'] == 'New Orleans, LA')]['cur_passengers'].sum()
   Passenger_cur2= da[(da['Year'] == 2008) & (da['city'] == 'New Orleans, LA')]['cur_passengers'].sum()
   Passenger_cur3= da[(da['Year'] == 2009) & (da['city'] == 'New Orleans, LA')]['cur_passengers'].sum()

   #storing the values in the form of dictionaries
   sr1={'City':['New Orleans, LA'],'Passengers':[Passenger_cur1],'Year':[2007]}
   sr2={'City':['New Orleans, LA'],'Passengers':[Passenger_cur2],'Year':[2008]}
   sr3={'City':['New Orleans, LA'],'Passengers':[Passenger_cur3],'Year':[2009]}

   #Converting dictionaries to datframe
   dr1=pd.DataFrame(sr1)
   dr2=pd.DataFrame(sr2)
   dr3=pd.DataFrame(sr3)

   plt.figure(figsize=(9, 6))

   #with the help of concat() we can combine two or more dataframe 
   dr=pd.concat([dr1,dr2,dr3])


   wx=sns.barplot(x='Year',y='Passengers',hue='Year',data=dr,palette='viridis')

   #Adding title and labels
   plt.title('Comparison of Passengers by year')
   plt.xlabel('Year')
   plt.ylabel('Passengers')
   for bars in wx.containers:
     wx.bar_label(bars)
```
<img src="https://github.com/user-attachments/assets/1e77d7ae-f011-4c5f-807c-17cac525b829" width="1200" height="1200">

```python
   #Filtering the mean value of fares for the particular year
   fares1_cur = da[(da['Year'] == 2007) & (da['city'] == 'New Orleans, LA')]['cur_fare'].mean()
   fares2_cur = da[(da['Year'] == 2008) & (da['city'] == 'New Orleans, LA')]['cur_fare'].mean()
   fares3_cur = da[(da['Year'] == 2009) & (da['city'] == 'New Orleans, LA')]['cur_fare'].mean()

   #storing the values as a dictionaries
   tr1={'City':['New Orleans, LA'],'Fares':[fares1_cur],'Year':[2007]}
   tr2={'City':['New Orleans, LA'],'Fares':[fares2_cur],'Year':[2008]}
   tr3={'City':['New Orleans, LA'],'Fares':[fares3_cur],'Year':[2009]}

   #converting dictionaries to dataframe
   pr1=pd.DataFrame(tr1)
   pr2=pd.DataFrame(tr2)
   pr3=pd.DataFrame(tr3)

   #combining the dataframe with the help of concat() method
   plt.figure(figsize=(9, 8))
   tr=pd.concat([pr1,pr2,pr3])


   sx=sns.barplot(x='Year',y='Fares',hue='Year',data=tr,palette='viridis')

   #Adding title and label
   plt.title('Comparison of Fares by year')
   plt.xlabel('Year')
   plt.ylabel('Fares')
   for bars in sx.containers:
      sx.bar_label(bars)
```
<img src="https://github.com/user-attachments/assets/2b2d7469-136f-45f2-8f19-7547d83487b8" width="1200" height="1200">

As This graph also prove that there is no relation with the airfare and passenger's count.

We calculate the correlation of the two datasets.Correlation is a statistical measure that expresses the extent to which two variables are linearly related (meaning they change together at a constant rate). It's a common tool for describing simple relationships without making a statement about cause and effect.

```python
   correlation = da['cur_fare'].corr(da['cur_passengers'])
   print(f'Correlation between Airfare and Passengers: {correlation}')
```
```text
   Correlation between Airfare and Passengers: 0.1735046284579055
```



# Conclusion

The positive correlation identified in our analysis indicates that as one variable increases, the other variable tends to increase as well. This relationship suggests a direct association between the two variables, implying that changes in one variable are systematically related to changes in the other. While the correlation does not imply causation, it provides valuable insights into the strength and direction of the relationship, which can inform further research and decision-making. Understanding this positive correlation allows for better predictions and strategic planning based on the observed patterns in the data.

a positive correlation between two variables means that they tend to increase together, but it doesn't necessarily imply that one variable causes the other to change. Other factors may also be responsible for the observed changes. 


# Future Work

Given the positive correlation between passenger count and airfare, future research should aim to understand this unexpected relationship. Key areas for investigation include:

## Causal Analysis:

  Experimental Studies: Conduct experiments to manipulate airfare and observe changes in passenger count, establishing if higher fares cause higher passenger counts.
  
  Longitudinal Studies: Track airfare and passenger count over time to determine the causality direction.
  
## Investigating Confounding Variables:

Identify other factors (e.g., economic conditions, seasonal effects, marketing strategies) that might influence both airfare and passenger count.

## Market Segmentation:

Analyze different market segments (e.g., business vs. leisure travelers) to see if the correlation varies across groups.

## Mechanistic Studies:

Study underlying mechanisms, such as perceived value, customer preferences, and service quality, that might explain the positive correlation.

## Replication and Validation:

Replicate the study in different regions or times to verify the robustness of the findings.

## Predictive Modeling:

Develop models to predict passenger count based on changes in airfare and other relevant variables.

## Interdisciplinary Research:

Collaborate with economists, sociologists, and marketing experts to gain a comprehensive understanding of the factors driving this correlation.

By exploring these areas, researchers can better understand the factors contributing to the positive correlation and develop strategies for optimizing pricing and increasing passenger numbers.

# Contribution 
  Data: `kaggle.com/datasets`
  Books: ` "A Python Data Analyst's Toolkit" by Gayathri Rajagopalan`


