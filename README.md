# ✈️ Consumer Airfare Data Analysis & Market Segmentation

## 📌 Project Overview

This project explores the Consumer Airfare Data Analysis & Market Segmentation! This notebook goes beyond basic analysis to deliver actionable insights through exploratory data analysis (EDA) and market segmentation of airfare trends across the U.S.

### 🎯 Objective

- Clean and preprocess airfare data
- Visualize airfare and passenger trends over the years
- Analyze patterns and draw meaningful conclusions about pricing and travel behavior
- Segment the air travel market based on Airfare and Passenger Volume

---

## 🛠️ Tools & Technologies

| Category       | Stack Used |
|----------------|------------|
| Programming    | Python (Pandas, Matplotlib, Seaborn) |
| Data Handling  | CSV, DataFrames |
| Visualization  | Matplotlib, Seaborn |
| Reporting      | Jupyter Notebook |
| Data Source    | [Kaggle - Consumer Airfare Report](https://www.kaggle.com/datasets) |

---


## 🔍 Dataset Description

| Column Name      | Description |
|------------------|-------------|
| `city`           | City name (with region) |
| `cur_fare`       | Current year average airfare |
| `ly_fare`        | Last year average airfare |
| `cur_passengers` | Current year passenger count |
| `ly_passengers`  | Last year passenger count |
| `distance`       | Trip distance in nautical miles |
| `year`, `quarter`| Date fields |
| `citymarketid`   | Unique ID per city |
| `trip_id`        | Trip reference ID |

---

## 📊 Key Steps

### 1. 📦 Data Cleaning & Preparation
- Removed null values and duplicate columns
- Converted `distance` from float to integer
- Renamed ambiguous columns for clarity
- Standardized city names

### 2. 📈 Exploratory Data Analysis
- Compared mean airfare vs. passenger count across four major cities
- Analyzed yearly changes for New Orleans from 2007–2009
- Used bar charts for comparative visual insights

### 3. 📉 Correlation Analysis
- Calculated Pearson correlation between airfare and passengers
- Found a **weak positive correlation** (0.17) suggesting limited dependency

---

## 📌 Business Insights

- Cities with high average fares (e.g. DC, LA) still maintained steady passenger counts
- Passenger volume increased over years despite slight fare hikes
- Pricing alone may not drive travel behavior — other factors (service, necessity, route demand) likely play a role
- Market segmentation revealed distinct customer groups based on fare and Passeneger Volume for targeted strategies.

---

## 📊 Visual Highlights

### 📊 Average Fare by City (Current vs Last Year)
![City Fare Comparison](Plots/ComparisonofFaresbycity.png)

### 👥 Passenger Count by Year (New Orleans)
![Passengers by Year](Plots/ComparisonofPassengerbyyear.png)

### 💰 Fare Trend by Year (New Orleans)
![Fares by Year](Plots/ComparisonofFaresbyyear.png)

---
Market Segmentation Based on Average Fare & Passenger Volume
To better understand market dynamics, we performed segmentation using two key metrics:

Average Fare – the cost to the consumer

Passenger Volume – the number of travelers between origin-destination pairs

This segmentation allows us to categorize city pairs (or routes) into strategic market segments based on cost sensitivity and traffic demand.

🎯 Segmentation Logic
By plotting and clustering data points using average fare on one axis and passenger volume on the other, we identified four primary segments:

Segment	Description
1. Premium High-Volume	High passenger volume and high average fares. These routes are strong revenue generators and likely include major business travel corridors.
2. Budget High-Volume	High passenger volume with low fares. These are price-sensitive, competitive markets — often targeted by low-cost carriers.
3. Premium Low-Volume	High fares but low passenger counts. These routes may serve niche or luxury markets and may require service optimization.
4. Budget Low-Volume	Low fares and low volume — potentially underperforming routes that may not be profitable without optimization or marketing.
   

---

## 📈 Result Summary

| Metric                      | Value         |
|----------------------------|---------------|
| Dataset Size               | ~6,699 rows    |
| Cities Analyzed            | 90+            |
| Correlation (Fare vs Pax)  | 0.1735 (weak +ve) |
| Trend                      | Passengers ↑ even as Fares ↑ slightly |
| Tool Used for Analysis     | Python, Jupyter, Seaborn |

---

## 🔮 Future Enhancements

- **Predictive Modeling**: Use regression or time-series to forecast fare elasticity
- **Market Segmentation**: Split analysis by business vs leisure travelers
- **External Factors**: Add fuel cost, holidays, competitor pricing
- **Interactive Dashboard**: Migrate insights to Power BI or Tableau

---

## 🙋🏻 Contribution & Acknowledgment

- Dataset: [Kaggle - Consumer Airfare](https://www.kaggle.com/datasets)
- Reference: *“A Python Data Analyst's Toolkit” by Gayathri Rajagopalan*
- Author: [Praveen S](mailto:praveen.s.analyst@gmail.com)

---

## 📎 Project Outcome

This project simulates the kind of ad-hoc and business-driven exploratory work often performed by data analysts in **retail, transport, or banking** sectors. It reflects proficiency in:

✅ EDA  
✅ Business interpretation  
✅ Visualization and storytelling  
✅ Report-ready documentation  
✅ Python workflow for real-world datasets

---

