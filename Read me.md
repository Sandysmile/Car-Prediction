# What Drive the Price of a Car?

Overveiw: 

In the application, I explored a car dataset from Kaggle. The orginal dataset contained 3 million used cars,
through the applcation, I adopt a standard process in industry for data projects called
CRISP-DM. 

![CRISP Model](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/CRISP%20Model.png)


Data: See the vehicles.zip file updated in the repository

Notebook: see the notebook file in the repository

Project Summary link: 

# Business Understanding/Goals

## Why? 
Car prices are determined by crucial car specifications such as cylinder count, fuel type, drive type, model, and manufacturer brands, complemented by aesthetic factors like paint colors. It also encompasses indicators of car condition and transferability such as the general condition, year, and odometer reading, and title status.

## What? 
Key features such as the manufacturer brand, year, odometer, model, and car condition are provided by the dataset to be significant predictors of a car's market price. These features largely capture the mechanical state and desirability of a car. 

## How? 
Insights from predictive models enable car dealerships to tailor inventory and marketing strategies to buyer preferences, enhancing business outcomes by aligning offerings, optiizing sales, and increasing profitability.

## Goal
1. To find the best model to predict the price of cars 
2. to presant the features that most influence price to car dealer



Data Understanding

# Data Structure 

 ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/Data%20Structure.png).
 
# Data Quality Check 

1. Check Missing Values in Three Ways
   
  1.1 Percentage of Missing Values for Each Variable

  ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/MissingValues.png). 

  1.2 Density of Missing Values across different variables (Panda Profiling Analysis)
  
  ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/ProfilingMissing%20Values.png). 

  1.3 Nulllity Correlations among varibles (Panda Profiling Analysis)
  
  ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/NullityCorrelation.png). 
  
  Please Note:
  30% of VIN numbers are missing. which points to potential issues in data capture, data quality, or the application of privacy filters. This significant gap necessitates extensive data cleanup or imputation, 
  which could potentially skew the insights derived from predictive models

  Over 70% of Size variable values are missing. Drop the Size varible for sure. 
  
2. High Cardinality
   
  ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/Cardinality.png) 


3. Imbalance in Categoircal Values
   
Take Fuel and Car Condition For Example 

![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/Imbalance.png) 
![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/CarCondition.png) 
  
7. Incorrect Feature Type - Convert Cylinder Into Numerical Varible
8. Code Car Condition into Ordinary Numbers 


9. Remove Zero Pricing Cars and Cars with Savaged Conditions
    
 ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/PriceOutlier.png) 
 ![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/BoxplotPrices.png) 
 

11. Remove Numerical Outliers Using Quantile Approach
![data overview](https://raw.githubusercontent.com/Sandysmile/Car-Prediction/main/Image/PricesScrewedness.png)

    


13. Distribution Skewness 
  
   
Numerical

Categorical 

Categorical to Numerical

Target Variable Price


Data Preparation

Remove Outliers

Correlations 

Prices with years, type, highlighted analysis

Modeling (4) 

Simple Linear Regression with Polynomial
Ridge 
Ridge with Polynomial
Lasso, SequentialFeatureSelector with Polynomial

Evaluation

Plot all model results

The best model is:
Ridge with Polynomial
Understand the coefficent, and importance. 


Feature analysis 
